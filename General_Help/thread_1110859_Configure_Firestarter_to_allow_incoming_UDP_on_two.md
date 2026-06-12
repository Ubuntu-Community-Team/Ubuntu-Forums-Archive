---
title: "Configure Firestarter to allow incoming UDP on two ports?"
date: 2009-03-30
forum: General Help
---

### Post by L a r r y on 2009-03-30
Hello all,

Running Ubuntu 8.04, on a computer behind a router firewall.  Made some extensive use of an amateur radio Internet-linking Windows software, EchoLink, recently, and it works quite well.  The firewall is configured to allow UDP incoming traffic to this computer on my network on ports 5198 and 5199, as required for EchoLink to accept connects from other users on the EchoLink network.

I decided to put a firewall on this computer, and downloaded and installed Firestarter.  This after I rebooted my computer once and was advised that my home folder was set to create-and-delete permissions across the board.  I have restored the folder permissions to a more restrictive create-and-delete/access-files/access-files, Execute checked.

I am more acquainted with read-and-write, read-only and execute terminology and the appropriate chmod values from my web development work than I am with the permissions terminology I see in the Ubuntu Properties sheet.

However, after restoring my 777 home folder to 755 and subfolders to 700 (create-and-delete/none/none, Execute checked), I decided to install a  firewall, and chose firestarter.

My question is, how do I configure this or any other recommended Linux firewall to allow incoming UDP traffic on ports 5198 and 5199?

I am able to connect with some stations on the network after having set a rule to allow connection with the IP address of one station, but this approach leaves it wide open, when I only need communication on two ports via UDP.

To further muddy my understanding of these things, I read a post that said running Firestarter or another 3-letter name, requires root permissions and adds to security risk. 

I am familiar with Windows and the use of ZoneAlarm Free to keep my Windows OS from being scanned by the many various port scanners.

I like the idea of running limited permissions and adding "sudo" in front of a command to gain temporary root privileges as needed, versus Windows' approach:  
Are you certain you want to do this?  Yes
Are you positive??  Yes.....

Any help is greatly appreciated.

---

### Post by lovinglinux on 2009-03-30
> **L a r r y said:**
> To further muddy my understanding of these things, I read a post that said running Firestarter or another 3-letter name, requires root permissions and adds to security risk. 

The problem with root permission is that former Windows users tend to use Firestarter to monitor connections, while they should only configure Firestarter and close it. When running it as root, there is a security risk that an attacker could gain control of your entire system. If you create the rules and close Firestarter, then you are fine.

Firestarter and UFW (3-letter name) are not actually firewalls. They are just firewall managers, which means they are tools for creating firewall rules for the built-in firewall framework (iptables+netfilter), without knowing how to use the required iptables commands. So once the rules are created, you can close the firewall manager because you will be protected by the real firewall.

The currently recommended firewall manager for beginners is UFW, which has a nice and simple GUI called GUFW. 

> **L a r r y said:**
> My question is, how do I configure this or any other recommended Linux firewall to allow incoming UDP traffic on ports 5198 and 5199?

Is actually pretty simple. First you need to block all incoming connections using the incomming firewall policy, then create a rule to open only the port/protocol you need. I don't remember exactly the steps, but should be pretty straight forward on both.

If you are in doubt if your settings are OK, then post the output of the command below, so we can analyze the iptables rules:

```
sudo iptables -L
```


> **L a r r y said:**
> I am able to connect with some stations on the network after having set a rule to allow connection with the IP address of one station, but this approach leaves it wide open, when I only need communication on two ports via UDP.

I guess you are worried that the remote IP would be able to connect to you on other ports. In this case, you just need to create rules based on port, not IP. Then you will fear that anyone else will be able to connect on those ports right? :)

Well, there is a big list of IPs that should connect to a port and you don't know all the originating addresses, then the best way to go is to open the port entirely. This is the way I do when using torrent, but I only open the port when the torrent client is active. Furthermore, I use [moblock]("http://moblock-deb.sourceforge.net/") to block known bad IPs.

If the list of IPs that should be allowed is not big and you know all their addresses, then you can create rules for those IPs individually, allowing access  to only one port or set of ports. This is the most secure and restrictive approach.

If you need a better control of connections, then you should learn [iptables ]("http://ubuntuforums.org/showthread.php?t=159661")commands. It is scary at first, but after a while you get used to it. Another option (recommended) is to use UFW, which allows a finer control over the rules without much iptables knowledge. Using a GUI like Firestarter or GUFW is easy and simple, but do not provide the same level of control and flexibility as with iptables commands.

---

### Post by hyper_ch on 2009-03-30
if you have a firewall on the router, why did you install firewall?

---

