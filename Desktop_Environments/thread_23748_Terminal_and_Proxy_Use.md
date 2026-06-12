---
title: "Terminal and Proxy Use"
date: 2005-04-03
forum: Desktop Environments
---

### Post by Sniffer on 2005-04-03
I think already someone have pointed this out but i'm as well behind a proxy in my laptop:

as you can see the result in my terminal when i try to install the automatic script:

# sudo sh ubuntusetup.sh
mv: cannot stat `sources.list': No such file or directory
gpg: can't get key from keyserver: Connection refused
gpg: Total number processed: 0
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.
ERROR # 2 : There was an error downloading the sources.list.


So i ask, how can i use my proxy connection in the terminal..or the way around how can i configure the terminal to use the proxy in order to use this script...???

Just for the info for instance, i have to configure my browser and synaptic to use the proxy...but can't find a way for the terminal

Thks
Sniff.

---

### Post by cwaldbieser on 2005-04-04
If you set the environment variable, HTTP_PROXY, equal to your proxy url, that should do it.  Case sensitivity might be a factor-- it might be http_proxy.  I can't recall at the moment.  For example:

```
$ export HTTP_PROXY=http://192.168.0.50:8080
$ export http_proxy=$HTTP_PROXY
```

should do the trick (substitute in your own proxy url).

---

### Post by ape on 2005-04-04
The variables that need to be set are:

  http_proxy=http://<your proxy host>:<your proxy port>
  
  and if your proxy handles ftp via http:

  ftp_proxy=http://<your proxy host>:<your proxy port>

---

### Post by Sniffer on 2005-04-04
Thnks you both for the help.

Just want to get smooth my ubuntu Hoary :-) 

and this script helps a lot.

Sniff.

---

### Post by Sniffer on 2005-04-11
The problem continue..... :-| 

root@ubuntu:/home/tiago # wget http://myosc.org/ubuntuguide/menueditor_0.4.3ubuntu1_all.deb
--18:48:52--  http://myosc.org/ubuntuguide/menueditor_0.4.3ubuntu1_all.deb
           => `menueditor_0.4.3ubuntu1_all.deb'
Resolving myosc.org... failed: Host not found.
root@ubuntu:/home/tiago #  http_proxy=http://192.168.0.1:6588 root@ubuntu:/home/tiago # export  http_proxy=http://192.168.0.1:6588 root@ubuntu:/home/tiago # export HTTP_PROXY=http://192.168.0.1:6588
root@ubuntu:/home/tiago # export http_proxy=$HTTP_PROXY
root@ubuntu:/home/tiago # ping google.pt
ping: unknown host google.pt
root@ubuntu:/home/tiago #

---

### Post by ape on 2005-04-27
So name resolution and your proxy have nothing to do with each other.  Have you verified that your DNS servers are set up properly in the /etc/resolv.conf file?  Is your default route set up?  Look at the output of the `netstat -rn` command.

Here's the IP address for google.pt -- 216.239.39.104
Can you ping the IP address and get a response back?  If not, there is something more fundementally wrong with your network.

---

### Post by sarimak on 2005-05-04
If you want to put the export xxx_proxy commands into a script you'll have to invoke that script via a bit unusual way that enables the environment variables (such as http_proxy) to be copied into the invoking shell (aka shell script sourcing).

ex:
. set_my_proxy

(see that dot and space before the script name - it isn't a typo)

If you roam across many proxified networks (work, home, customer, kiosk etc.) you may give the location as a parameter to that script...

Jirka

---

### Post by Blario on 2006-11-28
How would these two export commands that are given work if the http proxy used password authentication?  Can you set that?

---

### Post by oneofth3m on 2007-06-28
For password authentication use this....

export http_proxy="http://<username>:<password>@<proxy>:<port>"

ex:
export http_proxy="http://john:abcd@10.100.96.96:3128"

---

