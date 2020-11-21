##Download the binary
```
cd /tmp

wget https://github.com/prometheus/node_exporter/releases/download/v1.0.1/node_exporter-1.0.1.linux-amd64.tar.gz
```
## Extract the downloaded package. 
tar -xvf node_exporter-1.0.1.linux-amd64.tar.gz
```
cd node_exporter-1.0.1.linux-amd64
```
sudo mv node_exporter-1.0.1.linux-amd64/node_exporter /usr/local/bin/
```
sudo useradd -rs /bin/false node_exporter
```
sudo vi /etc/systemd/system/node_exporter.service
```
## Add this configuration in node_exporter.service
```   
vi node exporter.service

[Unit]
Description=Node Exporter
After=network.target

[Service]
User=node_exporter
Group=node_exporter
Type=simple
ExecStart=/usr/local/bin/node_exporter

[Install]
WantedBy=multi-user.target
```
## Reload the system daemon and start the node exporter service and enable it on boot system 

sudo systemctl daemon-reload

sudo systemctl start node_exporter

sudo systemctl status node_exporter

sudo systemctl enable node_exporter
