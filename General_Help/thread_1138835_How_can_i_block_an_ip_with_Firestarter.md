---
title: "How can i block an ip with Firestarter?"
date: 2009-04-26
forum: General Help
---

### Post by bigswagg on 2009-04-26
hi guyz.. i was wondering if any of you could help me block/remove this ip from my active connections. The ip is 74.6.104.11 i did a who is look up and here are the results.        what really bugs me is that the connections seems to be coming from yahoo.com and i am not connected to yahoo.com or yahoo msg. Is this something i should be worried about? maybe some kind of an intrusion? btw i went to the outbound traffic policy settings and denied connections to the host but that doesnt seem to be working at all. The ip still keeps showing up in my active connections. Any help will be gladly appreciated. :)

---

### Post by bigswagg on 2009-04-26
I apologize for the double post for some reason i am not able to properly edit the first post. Anyway here are the results of the who is IP look up

[IMG]http://img401.imageshack.us/img401/2366/screenshotegs.jpg[/IMG]

---

### Post by lovinglinux on 2009-04-26
Firestarter is not the best tool for monitoring connections and intrusion attempts. Besides, you don't have to keep Firestarter open to be protected. It is not the firewall, but just a firewall manager, which means it is a tool for configuring rules for iptables (the real firewall). Once you configure the rules, you can and should close it due to security reasons.

Additionally, it is not the recommended firewall manager anymore. It is kind of old and problems like this are more and more common.

You should try UFW, which is the current recommended firewall tool and installed by defaut. You can also install GUFW, which is the interface for UFW. To install, go to "Applications >> Add/Remove" and search for "gufw", select the program "Firewall Configuration" and click "Apply Changes".

If you decide to use gufw, is a good idea to remove Firestarter.

You should be able to block an IP from gufw.

You can also take a look at [moblock](http://moblock-deb.sourceforge.net/), which is an IP Blocker. It is basically like a firewall, but designed to block IPs only. It also has a GUI, called mobloquer.

---

### Post by doas777 on 2009-04-26
> **lovinglinux said:**
> Firestarter is not the best tool for monitoring connections and intrusion attempts. Besides, you don't have to keep Firestarter open to be protected. It is not the firewall, but just a firewall manager, which means it is a tool for configuring rules for iptables (the real firewall). Once you configure the rules, you can and should close it due to security reasons.

Additionally, it is not the recommended firewall manager anymore. It is kind of old and problems like this are more and more common.

You should try UFW, which is the current recommended firewall tool and installed by defaut. You can also install GUFW, which is the interface for UFW. To install, go to "Applications >> Add/Remove" and search for "gufw", select the program "Firewall Configuration" and click "Apply Changes".

If you decide to use gufw, is a good idea to remove Firestarter.

You should be able to block an IP from gufw.

You can also take a look at [moblock](http://moblock-deb.sourceforge.net/), which is an IP Blocker. It is basically like a firewall, but designed to block IPs only. It also has a GUI, called mobloquer.

not to hijack the thread, but i do have one basic frustration with gufw that firestarter does pretty well. How do you look at the blocked connections?

---

### Post by doas777 on 2009-04-26
is firestarter set to whitelist(default permit) or blacklist(default deny)?

---

### Post by bigswagg on 2009-04-26
thanks for your helpful reply lovinlinux :)

---

### Post by bigswagg on 2009-04-26
doas777 it is set to permissive by default, blacklist traffic.

---

### Post by doas777 on 2009-04-26
for terminating the connections, you can highlight and right click them to block the host. once they are disconnected, you want to create a rule for the whole block.

open firestaarter and go to the Policy tab and select Inbound Traffic Policy.
right click in the area that says "Block connections from host"
and select "add rule".
enter 74.6.0.0/16 as the network, and add a comment, then click ok, and the button to apply the policy change.

---

### Post by bigswagg on 2009-04-26
when i right click on any connections i only get the option of looking up host names and for Inbound Traffic Policy i see only the options for allowing connections from a host. If you were refering to Outbound traffic policy i have already done so and the ip still shows as active connection. Maybe i'll just go with ufw after all... wouldnt hurt to give it a shot :)  

any other suggestions fellow ubunters ?

---

### Post by doas777 on 2009-04-26
it sounds like you are whitelisting input and blacklisting output. classic stateful filtering.
you can add an output block, to stop connections from your host to the remote one, and it's already blocked from coming in unless your host initiates the connection.

you could kill the process listening on the port, restart networking, or reboot, to close the 
connections. since they are "Established" they pass through the stateful filter.

---

### Post by bigswagg on 2009-04-26
ty ty ty ty doas777 i was able to remove and block the ip from my active connections :)

so do you suggest i keep firestarter or move on to ufw? im asking since you seem to have experience with both wich one you prefer?

---

### Post by doas777 on 2009-04-26
I'm using gufw on boxes with newer distros, just because it is best to stay with the times. my only problem is that it doesn't provide any monitoring tools, so its only really useful for editing rules. I think it may be just a little too uncomplicated for my tastes. anyway I just use the traditional monitoring (netstat) and I've played with some conky scripts to show connections.

if you find a good firewall frontend, post back and let us know,
good luck

---

### Post by lovinglinux on 2009-04-26
> **doas777 said:**
> not to hijack the thread, but i do have one basic frustration with gufw that firestarter does pretty well. How do you look at the blocked connections?

Blocked connections can be followed by looking at the logs. First you need to add a line to the  /etc/syslog.conf  file, so that connection messages are logged on a separate file. This is not essential, but helps to filter other stuff.(if you don't do this then the next log path will be different)

```
kern.warning                     /var/log/iptables.log
```

Then run the following command in the terminal to see the blocked connections log in real time:

```
tail -f /var/log/iptables.log
```

If you use [screenlets](http://www.screenlets.org/index.php/Screenshots), you can add the command above to the "Startup Command" option of the "[TerminalScreenlet](http://screenlets.org/index.php/Terminal)" and you have a connection monitor on your desktop whenever you start the machine. I have several of them, each one monitoring a different log  8) 

To monitor allowed connections, I use IPTState (on a terminal screenlet too!)

```
sudo apt-get install iptstate
```

Run it on a terminal with 

```
sudo iptstate
```

I really don't know if IPTState is more secure or not, since it also runs as root and nobody answered this question yet. Anyways, it has several options for filtering by port, destination, source, state and TTL, toggled through the "b" key. It also allows you to terminate connections by simply selecting the connection then clicking "x". If you set a new iptables rule to block an specific IP, you can use IPTState to terminate the established connection, so the new rule won't be bypassed by the established state. I don't think Firestarter can do that. 8)

---

### Post by lovinglinux on 2009-04-26
> **bigswagg said:**
> ty ty ty ty doas777 i was able to remove and block the ip from my active connections :)

so do you suggest i keep firestarter or move on to ufw? im asking since you seem to have experience with both wich one you prefer?

I recommend moving to ufw. You see a lot of questions regarding Firestarter problems here, but you don't see many about ufw. Actually I don't remember seeing any lately. 

You can't block outgoing connections with ufw without modifying configuration files manually, but you shouldn't be worried about them. The important thing is to block incoming connections.

If you are whilling to learn something new, they you could try to understand the iptables commands and create your own firewall. I don't use firewall managers like Firestarter and UFW anymore. I use only moblock to block IPs and since it has a built it script for iptables, I have my own set of rules that are loaded by moblock when I boot.

Some interesting reading:
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)
[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

### Post by HermanAB on 2009-04-26
The manual way to block a connection is like this:
```
$ sudo iptables -I INPUT -i eth0 -s 74.6.104.11 -j DROP
```

---

### Post by bigswagg on 2009-04-26
ok i guess i am goin with ufw after all :) once again ty ty ty guyz for all your help you're  the best! Funny how i came here askin for a simple ip block and now i leave with all this good info. This kind of support you guys offer makes leaving XP so much easier. Have to say this is a great community and im just glad i can be part of it. 

                                                            VIVA UBUNTU!!!

[CENTER] :guitar:
[/CENTER]

---

### Post by lovinglinux on 2009-04-26
> **bigswagg said:**
> ok i guess i am goin with ufw after all :) once again ty ty ty guyz for all your help you're  the best! Funny how i came here askin for a simple ip block and now i leave with all this good info. This kind of support you guys offer makes leaving XP so much easier. Have to say this is a great community and im just glad i can be part of it. 

                                                            VIVA UBUNTU!!!

[CENTER] :guitar:
[/CENTER]

You are welcome. Eight months ago I was in the same spot you are today and the community was incredibly helpful. So now I give back my time to the community  8)

BTW, let us know later if you liked ufw.

---

### Post by doas777 on 2009-04-27
> **lovinglinux said:**
> Blocked connections can be followed by looking at the logs. First you need to add a line to the  /etc/syslog.conf  file, so that connection messages are logged on a separate file. This is not essential, but helps to filter other stuff.(if you don't do this then the next log path will be different)

```
kern.warning                     /var/log/iptables.log
```

Then run the following command in the terminal to see the blocked connections log in real time:

```
tail -f /var/log/iptables.log
```

If you use [screenlets](http://www.screenlets.org/index.php/Screenshots), you can add the command above to the "Startup Command" option of the "[TerminalScreenlet](http://screenlets.org/index.php/Terminal)" and you have a connection monitor on your desktop whenever you start the machine. I have several of them, each one monitoring a different log  8) 

To monitor allowed connections, I use IPTState (on a terminal screenlet too!)

```
sudo apt-get install iptstate
```

Run it on a terminal with 

```
sudo iptstate
```

I really don't know if IPTState is more secure or not, since it also runs as root and nobody answered this question yet. Anyways, it has several options for filtering by port, destination, source, state and TTL, toggled through the "b" key. It also allows you to terminate connections by simply selecting the connection then clicking "x". If you set a new iptables rule to block an specific IP, you can use IPTState to terminate the established connection, so the new rule won't be bypassed by the established state. I don't think Firestarter can do that. 8)

Thank you sir, I'll look into this tonight!

---

### Post by bigswagg on 2009-04-27
lovinglinux that is so cool of you to give back to the community. I admire that and hope to some day be able to do the same :) Anyways i managed to completely remove firestarter and install ufw. I then ran some commands in the terminal to enable ufw (sudo ufw enable & sudo ufw default deny) please correct me if this is wrong or if i did not need to do this. I then installed gufw and checked firewall enable and set the current configuration to deny incoming traffic. I have to say i like this much better and i feel when surfing the web pages load much quicker. If there are any other settings i should be worried about or that need to be configure please let me know. BTW guys i was wondering after uninstalling firestarter are there some kind of leftover junk? If so how can i remove these? Thanks in advance :)

---

### Post by lovinglinux on 2009-04-27
> **bigswagg said:**
> lovinglinux that is so cool of you to give back to the community. I admire that and hope to some day be able to do the same :) Anyways i managed to completely remove firestarter and install ufw. I then ran some commands in the terminal to enable ufw (sudo ufw enable & sudo ufw default deny) please correct me if this is wrong or if i did not need to do this. I then installed gufw and checked firewall enable and set the current configuration to deny incoming traffic. I have to say i like this much better and i feel when surfing the web pages load much quicker. If there are any other settings i should be worried about or that need to be configure please let me know. BTW guys i was wondering after uninstalling firestarter are there some kind of leftover junk? If so how can i remove these? Thanks in advance :)

You don't need to setup ufw with command-line if you are using the gui (gufw). They are just different methods of controlling the same thing. Nevertheless, you can use both if you want. Sometimes is faster to use command-line.

Denying incoming traffic is the most important thing. You might also check in the gufw interface if the firewall is set to load on boot. I guess there is an option to do that.

Since you removed Firestarter, there won't be any left overs that could affect your firewall.

---

### Post by bigswagg on 2009-04-28
Ok i guess i'll use either one & yes ufw is set to load on boot. Thanks again for all your help lovinglinux ;)

---

### Post by lovinglinux on 2009-04-28
> **bigswagg said:**
> Ok i guess i'll use either one & yes ufw is set to load on boot. Thanks again for all your help lovinglinux ;)

You are welcome.

---

