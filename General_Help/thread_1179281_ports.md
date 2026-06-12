---
title: "ports?"
date: 2009-06-05
forum: General Help
---

### Post by _Corsair_ on 2009-06-05
Why do most of the ports on my machine seem to be closed?  I wote this program to try to sequentially open a socket with every port on my machine:

```
import java.io.*;
import java.net.*;

public class locator{
public static void main(String[] args) throws IOException {
	Socket skt = null;
	int num = 0;
	while (true){
		try {
			skt = new Socket("localhost", num);
			System.out.println(num);
			skt.close();
			num++;
	        } catch (IOException e) {
			num ++;
			if (num == 65536)
				System.exit(1);
		}
	}
}
}
```
and the entire output is only a few numbers.  80 and 631 seem to be constant, but other high numbers come and go, sometimes only leaving the final two.  (Example: recent outputs: 80, 631, 33480, 54925 / 80, 631, 56478 / 80, 631 / 80, 631.) I was under the impression that most of the ports are not usually occupied, and that (x)ubuntu has no default firewall.  Netstat only lists several dozen ports in use, as does /etc/services.  What am I missing?  And why are ports becoming unusuable?  Thanks for any ideas!

Here's the verbose exception if you're interested:
```
Couldn't get I/O for the connection.
java.net.ConnectException: Connection refused
java.net.ConnectException: Connection refused
	at java.net.PlainSocketImpl.socketConnect(Native Method)
	at java.net.AbstractPlainSocketImpl.doConnect(AbstractPlainSocketImpl.java:310)
	at java.net.AbstractPlainSocketImpl.connectToAddress(AbstractPlainSocketImpl.java:176)
	at java.net.AbstractPlainSocketImpl.connect(AbstractPlainSocketImpl.java:163)
	at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:381)
	at java.net.Socket.connect(Socket.java:537)
	at java.net.Socket.connect(Socket.java:487)
	at java.net.Socket.<init>(Socket.java:384)
	at java.net.Socket.<init>(Socket.java:198)
	at sunex1.main(sunex1.java:12)

```

---

