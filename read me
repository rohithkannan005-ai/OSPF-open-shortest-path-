# OSPF Dynamic Routing - Multi-City Network

## 📋 Project Overview
This project demonstrates **OSPF (Open Shortest Path First)** dynamic routing protocol implementation across a 4-city network topology using Cisco Packet Tracer. Unlike static routing, OSPF automatically discovers and learns routes, providing dynamic path selection and network convergence.

## 🌐 Network Topology

```
                    OSPF AREA 0 (Backbone Area)
        ┌──────────────────────────────────────────────┐
        │                                              │
     Delhi ───────── Mumbai ───────── Kolkata ───────── Pune
    (2911)          (2911)           (2911)           (2911)
       │               │                 │               │
   Switch0         Switch1           Switch2         Switch3
  (2960-24TT)     (2960-24TT)       (2960-24TT)     (2960-24TT)
       │               │                 │               │
      PC0             PC1               PC2             PC3
```

![Network Topology](screenshots/ospf-topology.png)

### Network Architecture:
- **4 Cisco 2911 Routers** forming OSPF Area 0 (Backbone)
- **4 Cisco 2960-24TT Switches** for LAN connectivity
- **4 End Devices** (PC0-PC3) representing each city's network
- **Fully meshed topology** between routers for redundancy

## 🎯 Objectives
- Implement OSPF dynamic routing protocol
- Configure OSPF Area 0 (backbone area)
- Enable automatic route discovery and convergence
- Demonstrate link-state routing advantages
- Test network redundancy and failover

## 🔧 Configuration Details

### OSPF Configuration

#### Delhi Router
```cisco
Router>enable
Router#configure terminal
Router(config)#hostname Delhi
Delhi(config)#interface GigabitEthernet0/0
Delhi(config-if)#ip address 10.0.0.1 255.255.255.0
Delhi(config-if)#no shutdown
Delhi(config-if)#exit

Delhi(config)#interface GigabitEthernet0/1
Delhi(config-if)#ip address 192.168.1.1 255.255.255.0
Delhi(config-if)#no shutdown
Delhi(config-if)#exit

! Enable OSPF
Delhi(config)#router ospf 1
Delhi(config-router)#network 10.0.0.0 0.0.0.255 area 0
Delhi(config-router)#network 192.168.1.0 0.0.0.255 area 0
Delhi(config-router)#exit
```

#### Mumbai Router
```cisco
Router>enable
Router#configure terminal
Router(config)#hostname Mumbai
Mumbai(config)#interface GigabitEthernet0/0
Mumbai(config-if)#ip address 10.0.0.2 255.255.255.0
Mumbai(config-if)#no shutdown
Mumbai(config-if)#exit

Mumbai(config)#interface GigabitEthernet0/1
Mumbai(config-if)#ip address 20.0.0.1 255.255.255.0
Mumbai(config-if)#no shutdown
Mumbai(config-if)#exit

Mumbai(config)#interface FastEthernet0/0
Mumbai(config-if)#ip address 192.168.2.1 255.255.255.0
Mumbai(config-if)#no shutdown
Mumbai(config-if)#exit

! Enable OSPF
Mumbai(config)#router ospf 1
Mumbai(config-router)#network 10.0.0.0 0.0.0.255 area 0
Mumbai(config-router)#network 20.0.0.0 0.0.0.255 area 0
Mumbai(config-router)#network 192.168.2.0 0.0.0.255 area 0
Mumbai(config-router)#exit
```

#### Kolkata Router
```cisco
Router>enable
Router#configure terminal
Router(config)#hostname Kolkata
Kolkata(config)#interface GigabitEthernet0/0
Kolkata(config-if)#ip address 20.0.0.2 255.255.255.0
Kolkata(config-if)#no shutdown
Kolkata(config-if)#exit

Kolkata(config)#interface GigabitEthernet0/1
Kolkata(config-if)#ip address 30.0.0.1 255.255.255.0
Kolkata(config-if)#no shutdown
Kolkata(config-if)#exit

Kolkata(config)#interface FastEthernet0/0
Kolkata(config-if)#ip address 192.168.3.1 255.255.255.0
Kolkata(config-if)#no shutdown
Kolkata(config-if)#exit

! Enable OSPF
Kolkata(config)#router ospf 1
Kolkata(config-router)#network 20.0.0.0 0.0.0.255 area 0
Kolkata(config-router)#network 30.0.0.0 0.0.0.255 area 0
Kolkata(config-router)#network 192.168.3.0 0.0.0.255 area 0
Kolkata(config-router)#exit
```

#### Pune Router
```cisco
Router>enable
Router#configure terminal
Router(config)#hostname Pune
Pune(config)#interface GigabitEthernet0/0
Pune(config-if)#ip address 30.0.0.2 255.255.255.0
Pune(config-if)#no shutdown
Pune(config-if)#exit

Pune(config)#interface GigabitEthernet0/1
Pune(config-if)#ip address 192.168.4.1 255.255.255.0
Pune(config-if)#no shutdown
Pune(config-if)#exit

! Enable OSPF
Pune(config)#router ospf 1
Pune(config-router)#network 30.0.0.0 0.0.0.255 area 0
Pune(config-router)#network 192.168.4.0 0.0.0.255 area 0
Pune(config-router)#exit
```

### PC Configuration

| Device | IP Address | Subnet Mask | Default Gateway | Location |
|--------|------------|-------------|-----------------|----------|
| PC0 | 192.168.1.10 | 255.255.255.0 | 192.168.1.1 | Delhi |
| PC1 | 192.168.2.10 | 255.255.255.0 | 192.168.2.1 | Mumbai |
| PC2 | 192.168.3.10 | 255.255.255.0 | 192.168.3.1 | Kolkata |
| PC3 | 192.168.4.10 | 255.255.255.0 | 192.168.4.1 | Pune |

## ✅ Verification & Testing

### View OSPF Neighbors
```cisco
Router#show ip ospf neighbor
```
Expected output shows all adjacent routers with their Router IDs and states (FULL/DR, FULL/BDR, FULL/DROTHER).

### View OSPF Routing Table
```cisco
Router#show ip route ospf
```
Shows routes learned via OSPF (marked with 'O').

### Check OSPF Database
```cisco
Router#show ip ospf database
```
Displays Link State Database (LSDB) information.

### View OSPF Interface Information
```cisco
Router#show ip ospf interface
```
Shows OSPF-enabled interfaces, their states, and costs.

### Test Connectivity
From PC0 (Delhi):
```
C:\>ping 192.168.2.10  (Mumbai)
C:\>ping 192.168.3.10  (Kolkata)
C:\>ping 192.168.4.10  (Pune)
```

### Test Path Selection
```
C:\>tracert 192.168.4.10
```
Shows the dynamic path OSPF selected.

### Test Convergence
1. Disable a link between routers
2. Watch OSPF recalculate routes
3. Verify connectivity is maintained through alternate path

## 📊 IP Addressing Scheme

### WAN Links (Router-to-Router)
| Link | Router 1 | IP Address | Router 2 | IP Address | Network |
|------|----------|------------|----------|------------|---------|
| Link 1 | Delhi | 10.0.0.1 | Mumbai | 10.0.0.2 | 10.0.0.0/24 |
| Link 2 | Mumbai | 20.0.0.1 | Kolkata | 20.0.0.2 | 20.0.0.0/24 |
| Link 3 | Kolkata | 30.0.0.1 | Pune | 30.0.0.2 | 30.0.0.0/24 |

### LAN Networks
| City | Network | Router Interface | Gateway |
|------|---------|------------------|---------|
| Delhi | 192.168.1.0/24 | Gi0/1 - 192.168.1.1 | 192.168.1.1 |
| Mumbai | 192.168.2.0/24 | Fa0/0 - 192.168.2.1 | 192.168.2.1 |
| Kolkata | 192.168.3.0/24 | Fa0/0 - 192.168.3.1 | 192.168.3.1 |
| Pune | 192.168.4.0/24 | Gi0/1 - 192.168.4.1 | 192.168.4.1 |

## 🛠️ Equipment Used
- **Routers**: Cisco 2911 (x4)
- **Switches**: Cisco 2960-24TT (x4)
- **End Devices**: PC-PT (x4)
- **Cables**: Copper Straight-Through
- **Routing Protocol**: OSPF v2

## 📚 Key OSPF Concepts Demonstrated

### 1. **Link-State Routing**
- Each router builds complete topology map
- Uses Dijkstra's Shortest Path First (SPF) algorithm
- Better convergence than distance-vector protocols

### 2. **OSPF Area Design**
- Area 0 (Backbone Area) implementation
- All routers in single area for simplicity
- Scalable design for future multi-area expansion

### 3. **Dynamic Route Discovery**
- Automatic neighbor discovery via Hello packets
- No manual route configuration needed
- Routes update automatically when topology changes

### 4. **Cost-Based Path Selection**
- OSPF uses link cost (based on bandwidth)
- Automatically selects best path
- Load balancing across equal-cost paths

### 5. **Fast Convergence**
- Rapid response to topology changes
- Link-state updates propagate quickly
- Maintains network connectivity during failures

## 🔍 OSPF Advantages Over Static Routing

| Feature | Static Routing | OSPF Dynamic Routing |
|---------|----------------|---------------------|
| Configuration | Manual for each route | Automatic discovery |
| Scalability | Poor (high admin overhead) | Excellent (auto-scaling) |
| Convergence | Manual intervention needed | Fast & automatic |
| Path Selection | Fixed paths | Dynamic best-path selection |
| Fault Tolerance | Requires manual reconfiguration | Automatic failover |
| Loop Prevention | Manual design needed | Built-in loop prevention |

## 🚀 How to Run This Project
1. Download and install [Cisco Packet Tracer](https://www.netacad.com/courses/packet-tracer)
2. Clone this repository
3. Open the `ospf-topology.pkt` file
4. Enter **Simulation Mode** to visualize OSPF packet exchange
5. Test connectivity and observe OSPF convergence
6. Try disabling links to see automatic route recalculation

## 💡 Learning Outcomes
- Understanding OSPF link-state routing protocol
- Configuring OSPF areas and process IDs
- Analyzing OSPF neighbor relationships
- Interpreting OSPF routing tables and databases
- Troubleshooting OSPF adjacencies
- Comparing dynamic vs. static routing
- Implementing network redundancy and failover

## 🔧 Advanced Configurations (Optional)

### Configure Router Priority (for DR/BDR election)
```cisco
Router(config)#interface GigabitEthernet0/0
Router(config-if)#ip ospf priority 100
```

### Adjust OSPF Cost
```cisco
Router(config)#interface GigabitEthernet0/0
Router(config-if)#ip ospf cost 10
```

### Configure Passive Interface
```cisco
Router(config)#router ospf 1
Router(config-router)#passive-interface GigabitEthernet0/1
```

### Set Router ID Manually
```cisco
Router(config)#router ospf 1
Router(config-router)#router-id 1.1.1.1
```

## 🔍 Troubleshooting Tips
- **No OSPF neighbors?** Check interface status and OSPF network statements
- **Routes not appearing?** Verify OSPF process is running and areas match
- **Adjacency stuck in INIT?** Check for mismatched Hello/Dead timers
- Use `debug ip ospf events` to see OSPF activity (careful in production!)
- Verify MTU matches on both sides of link
- Check for access-lists blocking OSPF multicast (224.0.0.5, 224.0.0.6)

## 📊 OSPF Packet Types
1. **Hello** - Neighbor discovery and keepalive
2. **DBD (Database Description)** - Summary of LSDB
3. **LSR (Link State Request)** - Request specific LSAs
4. **LSU (Link State Update)** - Contains LSAs
5. **LSAck** - Acknowledges LSAs

## 📁 Repository Structure
```
ospf-dynamic-routing/
├── README.md
├── ospf-topology.pkt
├── screenshots/
│   ├── ospf-topology.png
│   ├── ospf-neighbors.png
│   └── routing-table.png
└── configs/
    ├── delhi-router-config.txt
    ├── mumbai-router-config.txt
    ├── kolkata-router-config.txt
    └── pune-router-config.txt
```

## 📧 Contact
Questions about OSPF or this project? Feel free to reach out!

## 📜 License
This project is for educational purposes.

---
**Note**: This project demonstrates enterprise-grade dynamic routing protocol implementation, showcasing advanced networking concepts beyond basic static routing.
