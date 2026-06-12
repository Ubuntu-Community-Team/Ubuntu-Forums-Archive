---
title: "UDP ports connectivity problems"
date: 2006-07-26
forum: Desktop Environments
---

### Post by benguin on 2006-07-26
Hi there,
I have been facing a problem connecting to a server application via UDP ports in Dapper Drake. I have a client-server app for controlling a robotic device, which runs the control code and listens for external commands on a UDP port. The client is a graphical application for controlling the robot, which sends data to this UDP port and thus establishes a remote control mechanism. There's also a simulator for the server, in case the real hardware is not available.

The code seems to run fine under Hoary and Breezy. With Dapper, the program does not seem to connect at all. Connection to the robot (a different computer, thats all it is) does not work, and neither to the simulator (running on the same computer). I do not have iptables active. Using 'netstat -upl', I see this for the server(called supervisor):
```

Proto Recv-Q Send-Q Local Address           Foreign Address         State       
udp        0      0 *:5000                  *:*                                19755/supervisor
udp        0      0 *:1500                  *:*                                19755/supervisor

```

and this for the client(called operator):
```

Proto Recv-Q Send-Q Local Address           Foreign Address         State       

udp        0      0 *:5000                  *:*                                19901/operator

```


1500 is a special port number used for a backup, but the main port is 5000. I can never get the programs to talk to each other. What am I doing wrong?

Thanks,
-B-

---

