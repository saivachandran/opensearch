  
Update the package
 ```
sudo apt update 
sudo apt install openjdk-11-jdk -y
```
Download and install the Elastic GPG key:
```
curl -fsSL https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo gpg --dearmor -o /usr/share/keyrings/elastic-archive-keyring.gpg
```

Add the Elastic APT repository for version 7.x:
```
echo "deb [signed-by=/usr/share/keyrings/elastic-archive-keyring.gpg] https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-7.x.list
```

3. Pin Elasticsearch Version
```
echo "Package: elasticsearch Pin: version 7.10.2 Pin-Priority: 1001" | sudo tee /etc/apt/preferences.d/elasticsearch
```

5. Install Elasticsearch
```
sudo apt-get update 
sudo apt-get install elasticsearch=7.10.2
```

7. Configure Elasticsearch

```
sudo nano /etc/elasticsearch/elasticsearch.yml
discovery.type: single-node
node.name: node-1
network.host: 0.0.0.0
```

9. Start and Enable Elasticsearch
```    
sudo systemctl start elasticsearch sudo systemctl enable elasticsearch
sudo systemctl status elasticsearch
```

11. Verify Installation
```
curl -X GET "localhost:9200"
```
 
 
restore
 
sudo apt  install awscli
 
```  
to verfify
echo $AWS_ACCESS_KEY_ID
/usr/share/elasticsearch/bin/elasticsearch-keystore add s3.client.default.access_key
/usr/share/elasticsearch/bin/elasticsearch-keystore add s3.client.default.secret_key
sudo /usr/share/elasticsearch/bin/elasticsearch-plugin install repository-s3
curl -X POST http://localhost:9200/_nodes/reload_secure_settings
sudo systemctl restart elasticsearch
du -sch /var/lib/elasticsearch
to authenticate
curl -X PUT "http://localhost:9200/_snapshot/animaker-dev-es" -H 'Content-Type: application/json' -d '{"type": "s3", "settings": {"bucket": "anim-es-snap", "region": "us-west-2"}}'
```

