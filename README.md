## Cisco Switch Commands Cheatsheet
  en/enable = Enter config mode

Gi =  1 Gb
Twe = 10 Gb

**Create VLAN**
```
conf t
    vlan VLANID = Create VLAN 
        name NAME = Name on VLAN
        description DESCRIPTION = Description for VLAN
```

**Delete VLAN**
```
conf t
    no vlan 600 = Remove VLAN 600
```
**Reset port to default settings**
```
conf t
    default interface Gi1/0/xx
```

**Set port in trunk mode and allow all VLAN**
```
conf t
    interface Gi1/0/xx
    interface range Gi1/0/2
    switchport mode trunk
```

**Set port in trunk mode with native VLAN for untagged traffic + only allow certain VLAN through trunk**
```
conf t
    interface Gi1/0/xx OR interface range Gi1/0/2
    switchport mode trunk
    switchport trunk native vlan xxx
    switchport trunk allowed vlan xx,xx-xx,xx
```

**Set port in access mode (traffic is tagged when reaching the switch)**
```
conf t
    interface INTERFACE
    switchport access vlan 3006
    switchport mode access
```

**Exclude IP address from been distributed by DHCP**
```
conf t

ip dhcp excluded-address x.x.x.x
```

**Configure a DHCP pool on a VLAN**
```
conf t
    ip dhcp pool vlan3006
    network 10.3.6.0 255.255.255.0
    default-router 10.3.6.1
    dns-server 10.1.238.2 10.1.238.3
```

**Show DHCP pool configuration**
```
show ip dhcp pool xxx
```

**Enable or disable one or more interfaces**
```
conf t
    interface Gi1/0/xx
    interface range Gi1/0/2
    shutdown/no shutdown
```

**Show a list of all interfaces**
```
show interface status
```

**Show status on interface**
```
show interface INTERFACE

e.g. show interface Gi1/0/25
```

**Show MAC address for IP addresses**
```
show ip arp
```

**Show MAC address attached to a interface**
```
show mac address-table interface xx1/0/xx
```

**Lists all VLAN**
```
show vlan
```

**Visar current configuration on port**
```
show run int INTERFACE
```

**Show log**
```
show log
```

**Show current leased IP adresses**
```
show ip dhcp binding
```

**Show all interface that have a IP address attached**
```
show ip interface brief
```

**Active built-in DHCP server**
```
service dhcp
```

**Save current configuration**
```
copy running-config startup-config
```

**Show current configuration**
```
show running-config
```

**Show current configuration but include or exclude info**
```
show run | inc/exc/sec XXX
```