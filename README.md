## Routing

### Firewall A
#### eth0
IP: 141.20.35.66  
Subnetmask: 255.255.255.252  
Default-Gateway: 141.20.35.65

#### eth1
IP: 10.0.0.2  
Subnetmask: 255.255.255.0

### Squid/Bind
IP: 10.0.0.3  
Subnetmask: 255.255.255.0  
Default-Gateway: 10.0.0.2  
Gateway 10.0.1.* = 10.0.0.5

### Apache
    auto lo eth1  
    iface eth1 inet static  
	    address 10.0.0.1  
	    netmask 255.255.255.0  
	    gateway 10.0.0.2

    Ziel            Router          Genmask         Flags Metric Ref    Use Iface  
    default         10.0.0.2        0.0.0.0         UG    100    0        0 eth1  
    10.0.0.0        *               255.255.255.0   U     0      0        0 eth1

### Firewall B
#### eth0
IP: 10.0.0.4  
Subnetmask: 255.255.255.0  
Default-Gateway: 10.0.0.2  

#### eth1
IP: 10.0.1.1  
Subnetmask: 255.255.255.0

### Client
IP: 10.0.1.2  
Subnetmask: 255.255.255.0
