---
title: "stopping the firestarter firewall restart"
date: 2008-12-21
forum: General Help
---

### Post by jesse c on 2008-12-21
When my system times out after about 20 mins.of unuse(?) it goes to a black screen with the "stopping the firestarter firewall" statement with a blinking dash mark.I cant figure out how to restart so i hard kill by holding the power button.Anybody know the 'right' way to restart?

---

### Post by lovinglinux on 2008-12-21
First of all, you should configure the screensaver and power management preferences, to give more time before considering the computer as idle (or turn this feature off completely). You can do this in through the "System >> Preferences" menu.

Second and most important, you shouldn't run Firestarter all the time. Once you configure Firestarter rules, you don't have to keep it running. Firestarter is just a firewall manager, which means it is graphical interface for easily create iptables (the real firewall) rules. While Firestarter is awesome, some people say it has bugs that could allow a hacker to control your machine as root. This happens because Firestarter runs as root.  So, all you have to do is make sure the rules created by Firestarter are loaded after a reboot, then you don't even have to open Firestarter GUI anymore, if you don't need change the rules. If you do, then open Firestarter, change the rules and close it again.

Anyway, if the problem persist, try pressing CTRL+ALT+BACKSPACE. This will kill your session and log you off, so you can log in again without rebooting the machine.

---

### Post by 243kof on 2008-12-22
This happens when your system tries to suspend / hibernate. I know because I face the same bug when I try (by choice) to suspend or hibernate my computer. It just hangs there with the only message being "Stopping the Firestarter firewall..". I have installed Firestarter, but run it only when I want to change a rule. In System Monitor there is no process named "Firestarter". I haven't found any solution yet...

---

### Post by hyper_ch on 2008-12-22
firestarter is no firewall... are you even sure you need to run alternate rules anyway on the firewall?

---

### Post by 243kof on 2008-12-22
I know Firestarter is just a GUI, and yes I do need to change some things, open some ports, enable some services etc. Anyway, back to the issue, I tried stopping the firestarter service manually before suspending the machine with "sudo /etc/init.d/firestarter stop" and I got the same hang, same message. Maybe it's unrelated to firestarter after all?

---

### Post by chris7273 on 2009-01-19
I have the same problem : impossible to hibernate ou suspend.
Same message and frozen black screen

My pc is a shuttle SN95G5. 

Firestarter is installed but not running (checked in the running processes)

---

### Post by hyper_ch on 2009-01-19
you should use (g)ufw... Firestarter hasn't been maintained for years and the new standard - at least by Canoncial - is (g)ufw.

---

### Post by chris7273 on 2009-01-19
Thank you gor this info. I am a beginner with Linux and Ubuntu and I didn't know that there was an alternative to firestarer.

If I understand well, I should remove firestarter (with Synaptic) and then install the 2 programs "ufw" and "gufw". 

I am worried : Will I loose the router configuration performed with firestarter if I remove this one ? (port configuration for "amule" for example)

If someone could clarify this before I cry if I try this at home this evening (Morning now in Belgium)

Thank you

---

### Post by mcduck on 2009-01-19
> **243kof said:**
> I know Firestarter is just a GUI, and yes I do need to change some things, open some ports, enable some services etc. Anyway, back to the issue, I tried stopping the firestarter service manually before suspending the machine with "sudo /etc/init.d/firestarter stop" and I got the same hang, same message. Maybe it's unrelated to firestarter after all?

Actually Firestarter is not just a GUI. I know that this is a common thing to say, usually when somebody wants to run the Firestarter GUI all the time. There are 3 parts to the firewall when you use Firestarter: iptables/netfilter, Firestarter script and then the firestarter GUI for configuring the firewall.

Iptables/netfilter is not a firewall, it's a set of tools & features used to create a firewall.

Firestarter script is the firewall, starting automatically on boot, and using iptables/netfilter to manage your network traffic.

Firestarter GUI is the configuration tool, used to configure the Firestarter script (not iptables itself, if you'd do that you'd loose all firewall rules and settings on next boot)

But yes, I agree that it's a good idea to use Gufw instead of the old and unmaintained Firestarter.

---

### Post by mcduck on 2009-01-19
> **chris7273 said:**
> Thank you gor this info. I am a beginner with Linux and Ubuntu and I didn't know that there was an alternative to firestarer.

If I understand well, I should remove firestarter (with Synaptic) and then install the 2 programs "ufw" and "gufw". 

I am worried : Will I loose the router configuration performed with firestarter if I remove this one ? (port configuration for "amule" for example)

If someone could clarify this before I cry if I try this at home this evening (Morning now in Belgium)

Thank you

Your router is configured in the *router*. Whatever you do or run in your computer has nothing to do with what the router does. Changing your firewall will not change the routers settings. Just like disconnecting your computer from the router will not change the router's setting.

However I wonder how on earth you could configure your *router* with Firestarter? I bet you are now talking about port settings in firewall, not anything related to routers (those small boxes with loads of network connectors and possibly a WLAN access point)..

In that case yes, you will have to configure your firewall's port settings again if you change to using a different firewall.

Anyway, it should be mentioned here that most likely you don't need a firewall at all in Ubuntu. In the default setup there are no services running that would respond to incoming network connections. Unless you install some server you shouldn't need a firewall. (it makes no difference if a port is closed or not if nothing's listening to that port).

---

### Post by hyper_ch on 2009-01-19
for ufw have a look here: [http://tinyurl.com/8w7rp5](http://tinyurl.com/8w7rp5)

---

### Post by chris7273 on 2009-01-19
Mcduck : Thank you for the answer.  And also thank you for your patience  with newbies like me. I wrote "router" but I meant the ports that I opened in Firestarter.
So : 
- my router is configured (and independant from the PC, I knew it)
- I am going to remove firestarter 
- Install ufw and gufw
- open the ports in gufw (the ones that were previously configured in firestarter)
- Try again to launch hibernation and say a little prayer

If I forget sth important, please correct me.

Thank you

---

### Post by S0m3th1ngw13rd on 2009-01-19
So after I open Firestarter and set a few outtbound rules I can close it. Right now its running in the system tray area(not sure what its called in Linux yet. After exiting firestarter it is still blocking ports and such?

---

### Post by lovinglinux on 2009-01-20
> **S0m3th1ngw13rd said:**
> So after I open Firestarter and set a few outtbound rules I can close it. Right now its running in the system tray area(not sure what its called in Linux yet. After exiting firestarter it is still blocking ports and such?

Yes, but you need to make sure Firestarter scripts starts at boot, otherwise it will be turned off by default when you restart the machine.

---

### Post by chris7273 on 2009-01-21
OK my firestarter is now gone and replaced bu gufw and ufw. The initial problem is still there : 
When the computers goes to "suspend" or "hibernate", I get a black screen. The sentence "stopping firestarter" has disappeared but now I have a blinking white "underscore" symbol at the upper left on a black screen. 
When it goes to suspend : I hear a noise in my PC, it seems the hard drives are stopping but then nothing else happens and it is stuck. 
When it goes to hibernate : nothing happens but the black screen...
Any idea how I can activate this ?

My PC : shuttle XPC SN95G5, 2x256 Ram (Dual channel), one ide hard disk (where the old windows xp is installed) and one sata hard disk (where linux is installed)

---

### Post by hyper_ch on 2009-01-21
I still tend to think that in moste cases altering default iptables rules are not necessary...

---

### Post by mcduck on 2009-01-21
> **hyper_ch said:**
> I still tend to think that in moste cases altering default iptables rules are not necessary...

There *are* no default iptables rules.

All rules given to iptables will disappear on boot. If you want a firewall, you need some way to set the rules after the boot, and that's what all firewall scripts do. They store the rules you have set and enable them after every boot. (more advanced firewall scripts will also monitor the traffics all the time and change the rules on-the-fly, for example to prevent denial-of-service attacks.)

On out-of-yhe-box ubuntu setup there is no such scripts or services running, thus, no firewall. This is very easy to confirm; on a freshly installed Ubuntu machine (or one where you haven't installed any firewall, or enabled ufw) run "sudo iptables -L" to list iptables rules. You'll see that all traffic is allowed:
```
$ sudo iptables -L
[sudo] password for mcduck: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
$
```

Now I'll enable ufw and list the rules again:
```
$ sudo ufw enable
Firewall started and enabled on system startup
$ sudo iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ufw-before-forward  all  --  anywhere             anywhere            
ufw-after-forward  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ufw-before-output  all  --  anywhere             anywhere            
ufw-after-output  all  --  anywhere             anywhere            

Chain ufw-after-forward (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK FORWARD]: ' 
RETURN     all  --  anywhere             anywhere            

Chain ufw-after-input (1 references)
target     prot opt source               destination         
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-ns 
RETURN     udp  --  anywhere             anywhere            udp dpt:netbios-dgm 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:netbios-ssn 
RETURN     tcp  --  anywhere             anywhere            tcp dpt:microsoft-ds 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootps 
RETURN     udp  --  anywhere             anywhere            udp dpt:bootpc 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK INPUT]: ' 
RETURN     all  --  anywhere             anywhere            

Chain ufw-after-output (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ufw-user-forward  all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED 
DROP       all  --  anywhere             anywhere            ctstate INVALID 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp source-quench 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request 
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootps dpt:bootpc 
ufw-not-local  all  --  anywhere             anywhere            
ACCEPT     all  --  BASE-ADDRESS.MCAST.NET/4  anywhere            
ACCEPT     all  --  anywhere             BASE-ADDRESS.MCAST.NET/4 
ufw-user-input  all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ACCEPT     udp  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED 
ufw-user-output  all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type LOCAL 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type MULTICAST 
RETURN     all  --  anywhere             anywhere            ADDRTYPE match dst-type BROADCAST 
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 10 LOG level warning prefix `[UFW BLOCK NOT-TO-ME]: ' 
DROP       all  --  anywhere             anywhere            

Chain ufw-user-forward (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain ufw-user-input (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            limit: avg 3/min burst 5 LOG level warning prefix `[UFW LIMIT]: ' 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain ufw-user-output (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            
$

```
(In this case I didn't bother with setting default policy or any other rules with ufw, this should be enough to show the difference between having a firewall and not having one)

Now, this still doesn't mean that you'd need to do anything. The default install of Ubuntu has no running services that would respond to incoming network connections, which means that there's no holes you'd need to protect with a firewall.

(I disabled ufw again after doing this, since I don't need a firewall. My iptables is once again without any rules, all traffic is allowed.)

edit:
You can read more about iptables here: [https://help.ubuntu.com/community/IptablesHowTo]("https://help.ubuntu.com/community/IptablesHowTo")
and about ufw: [http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html]("http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html")

---

### Post by hyper_ch on 2009-01-21
> **mcduck said:**
> There *are* no default iptables rules.

and that is good ;) I should have stated the default iptables configuration ;)

---

### Post by mcduck on 2009-01-21
> **hyper_ch said:**
> and that is good ;) I should have stated the default iptables configuration ;)Agreed.

If it's not broken, don't fix it. Applies to security as well as anything else. :)

---

### Post by 243kof on 2009-01-21
Please guys, this was a discussion about a suspend/hibernate issue. Now that we've determined that the message "Stopping the firestarter firewall..." is (probably) unrelated, could we please stop debating about firestarter / ufw / iptables and focus to the actual problem? ;)

---

### Post by chris7273 on 2009-01-22
Yes, please.

I am still stuck with hibernation / suspension

I have tried some other "tricks" (uswsusp, powersaved, ...) but as I am a beginner, I think that I am going to stop trying things that I don't understand.

If someone as a solution...

---

### Post by geezerone on 2009-01-25
> **hyper_ch said:**
> for ufw have a look here: [http://tinyurl.com/8w7rp5](http://tinyurl.com/8w7rp5)

:lolflag: Like it!

---

### Post by Yleeyas on 2009-01-27
Hi Chris7273,
I have the exact same problem with suspend as you last described in post #15 above. I've been looking for similiar threads, but there are no solutions being offered, and I can't find anything useful in launchpad yet.
Might look at submitting a new bug report against 'power-management' or maybe 'kernel'.

Thanks to 243kof for trying to stop the thread hijack but, since this is 6 days old, I guess they killed the thread. I barely got thru to #15 to see the op's problem matched mine. Oh well.

---

### Post by chris7273 on 2009-01-29
OK, it seems that there's no solution. With Windows XP, the hibernation was working so I still have a little hope : it's not related to my hardware but well to the OS.

---

