# Web Server Network Configuration

A simple **Web Server Network** created and configured in **Cisco Packet
Tracer**.

## Project Overview

This project demonstrates how a client PC accesses a web page hosted on
a Web Server through a network switch. A separate DNS Server is used for
domain name resolution.

### Network Topology

``` text
PC0 (192.168.1.3)
        |
        |
    Switch-PT
      /     \
     /       \
Web Server   DNS Server
192.168.1.2  192.168.1.1
```

## IP Addressing

| Device     | IP Address  | Subnet Mask   | Role           |
|------------|-------------|---------------|----------------|
| DNS Server | 192.168.1.1 | 255.255.255.0 | DNS Server     |
| Web Server | 192.168.1.2 | 255.255.255.0 | Web Server     |
| PC0        | 192.168.1.3 | 255.255.255.0 | Client PC      |
| Switch-PT  | Layer 2     | N/A           | Network Switch |

## Devices Used

- 1 × PC-PT
- 1 × Switch-PT
- 2 × Server-PT
  - Web Server
  - DNS Server
- Copper Straight-Through cables

## Web Server Configuration

Web Server:

``` text
IP Address: 192.168.1.2
Subnet Mask: 255.255.255.0
```

In Cisco Packet Tracer:

``` text
Web Server → Services → HTTP
```

Enable the **HTTP** service.

## index.html Configuration

Edit the `index.html` file in the HTTP service:

``` html
<html>

<h1>Hi</h1>

<h2>cisco website</h2>

</html>
```

An image can be added manually to the web page.

## DNS Server Configuration

DNS Server:

``` text
IP Address: 192.168.1.1
Subnet Mask: 255.255.255.0
```

Go to:

``` text
DNS Server → Services → DNS
```

Enable DNS and create a record that points the selected domain name to:

``` text
192.168.1.2
```

Example:

``` text
Domain Name: cisco.local
IP Address: 192.168.1.2
```

## PC0 Configuration

``` text
IP Address: 192.168.1.3
Subnet Mask: 255.255.255.0
DNS Server: 192.168.1.1
```

A default gateway is not required for communication within this single
LAN.

## Testing

### Test 1: DNS Server

From PC0:

``` text
ping 192.168.1.1
```

Expected: successful replies.

### Test 2: Web Server

From PC0:

``` text
ping 192.168.1.2
```

Expected: successful replies.

### Test 3: Website Using IP Address

Open:

``` text
PC0 → Desktop → Web Browser
```

Enter:

``` text
http://192.168.1.2
```

The configured `index.html` page should appear.

### Test 4: Website Using DNS

If the DNS record is `cisco.local`, enter:

``` text
http://cisco.local
```

The DNS Server resolves the name to `192.168.1.2`, and the browser
accesses the Web Server.

## Working

``` text
PC0
 ↓
Switch-PT
 ↓
DNS Server
 ↓
Domain Name → 192.168.1.2
 ↓
Web Server
 ↓
HTTP Response
 ↓
PC0 Browser
```

**DNS** provides name resolution, while **HTTP** provides the web page.

## Screenshots

Recommended screenshots:

1.  Network topology
2.  PC0 IP configuration
3.  Web Server IP configuration
4.  HTTP service
5.  `index.html`
6.  DNS configuration
7.  DNS record
8.  Ping test
9.  Final website in PC0 browser

Recommended folder:

``` text
screenshots/
├── topology.png
├── pc0-ip-config.png
├── web-server-ip.png
├── http-config.png
├── index-html.png
├── dns-config.png
├── dns-record.png
├── ping-test.png
└── website-output.png
```

## Project Files

``` text
Web-Server-Network/
├── Web-Server-Network.pkt
├── README.md
└── screenshots/
```

## Software Used

- Cisco Packet Tracer

## Learning Outcomes

- Understanding basic LAN connectivity
- Configuring IPv4 addresses
- Understanding the role of a network switch
- Configuring a Web Server
- Enabling HTTP service
- Editing an `index.html` file
- Configuring DNS
- Understanding DNS name resolution
- Testing connectivity using `ping`
- Accessing a web server using a browser

## Author

**Utsav**

## Project Type

**Computer Networks - Cisco Packet Tracer Project**
