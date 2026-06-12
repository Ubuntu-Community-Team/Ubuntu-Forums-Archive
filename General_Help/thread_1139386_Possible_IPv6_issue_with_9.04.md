---
title: "Possible IPv6 issue with 9.04"
date: 2009-04-27
forum: General Help
---

### Post by cybrsaylr on 2009-04-27
Did the upgrade online from 8.10 to 9.04.
All went through OK and am using 9.04.

Only problem so far is internet access is slow loading pages.
This happened in the past when upgrading to newer versions of Ubuntu and found out it was an issue with Ipv6 that I had to disable to speed things up.

Here was the FIX:

> FIX:
found in Ubuntu help:

3.2.7. IPv6 Not Supported

1. IPv6 is supported by default in Ubuntu and can sometimes cause problems.
2. To disable it, open a Terminal (Applications &#9656; Accessories &#9656; Terminal) and type the command: gksudo gedit /etc/modprobe.d/aliases.
3. Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
4. Reboot Ubuntu.

Tried this FIX with 9.04 and it dosen't work, it just leaves you with a blank terminal page with no way to turn it to 'off'.

Does anyone know what the solution is, to speed up internet access again?

---

### Post by wil on 2009-04-27
I have the same problem on a fresh install

---

### Post by kpkeerthi on 2009-04-27
You might want to try these suggestions:

[http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html]("http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html")

[http://ubuntuforums.org/showpost.php?p=2810501&postcount=17]("http://ubuntuforums.org/showpost.php?p=2810501&postcount=17")

Remember to reboot for the changes to take effect.

---

### Post by wil on 2009-04-27
Thanks kpkeerthi

I replaced the network card and things seem much faster now.

Maybe it was not so IPV6 compatible.

---

### Post by cybrsaylr on 2009-04-27
> **kpkeerthi said:**
> You might want to try these suggestions:

[http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html]("http://www.ubuntu-inside.me/2009/04/howto-disable-ipv6-at-ubuntu-jaunty.html")

[http://ubuntuforums.org/showpost.php?p=2810501&postcount=17]("http://ubuntuforums.org/showpost.php?p=2810501&postcount=17")

Remember to reboot for the changes to take effect.

Tried the first solution in Terminal and didn't get the big 0
got this as showing Ipv6 is disabled:

> bash: /proc/sys/net/ipv6/conf/all/disable_ipv6: Permission denied


Tried the second solution but couldn't figure it out as yet....

Still have an awful lag with JJ.
Had this same lag with II and HH but once IPv6 was disabled everything sped back up to normal.

---

### Post by Brandon Williams on 2009-04-27
This is just a guess, but it looks like you may have attempted to execute the disable_ipv6 file as if it were a program. Please go back and try the first suggestion again. It wants you to run the program cat on the file /proc/sys/net/ipv6/conf/all/disable_ipv6. The '$' in the example represents the '$' at the end of the prompt on the command line. You aren't actually supposed to type it in.

If this isn't actually the problem, please cut-and-paste from the terminal so that we can see what you are typing in and the result.

---

### Post by cybrsaylr on 2009-04-27
Brandon Williams,
OK, when I try the first solution again without the [ $ ] I do get the big 0 meaning Ipv6 is enabled.

Then frankly, the rest of the directions in that 1st solution are confusing and poorly written. 

Not really sure what they mean or want...:confused:

---

### Post by cybrsaylr on 2009-04-27
> **Brandon Williams said:**
> If this isn't actually the problem, please cut-and-paste from the terminal so that we can see what you are typing in and the result.

Here's the results:

tt@tt-desktop:~$ cat /proc/sys/net/ipv6/conf/all/disable_ipv6
0
tt@tt-desktop:~$ sudo su -
[sudo] password for tt: 
root@tt-desktop:~# echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6
root@tt-desktop:~#


I reboot and no change, 9.04 still runs slow.

---

### Post by Brandon Williams on 2009-04-27
Run this command:
```
sysctl net.ipv6.conf.all.disable_ipv6
```

If the output is:
```
net.ipv6.conf.all.disable_ipv6 = 0
```

Then run this command to attempt to disable ipv6:
```
sudo sysctl -w net.ipv6.conf.all.disable_ipv6=1
```
Type in your password when asked.

Now test to see if the ipv6-related issue has gone away. If the problem is now resolved, then open /etc/sysctl.conf with nano:
```
nano /etc/sysctl.conf
```
And then add this line to the bottom of the file:
```
net.ipv6.conf.all.disable_ipv6 = 1
```

Reboot and test to see whether your problem has cleared up.

I haven't done this myself, because I don't actually need to have ipv6 disabled. However, it has a chance of success. Let us know if it works.

---

### Post by cybrsaylr on 2009-04-27
> **Brandon Williams said:**
> Run this command:
```
sysctl net.ipv6.conf.all.disable_ipv6
```

Ran that and got this right off:

tt@tt-desktop:~$ sysctl net.ipv6.conf.all.disable_ipv6
net.ipv6.conf.all.disable_ipv6 = 1

Rebooted and things are still slow.

---

### Post by Brandon Williams on 2009-04-27
Either the problem is not ipv6 or the sysctl setting is not working to disable ipv6.

Run this command, replacing eth1 with whatever your active interface designation is:
```
sudo tcpdump -i eth1 ip6
```

Now surf to a URL that has been running slowly for you. Is there any output from tcpdump when you do this? And if so, what does the output look like?

If there's no output, that means that ipv6 isn't doing anything.

---

### Post by cybrsaylr on 2009-04-27
> **Brandon Williams said:**
> Either the problem is not ipv6 or the sysctl setting is not working to disable ipv6.

Run this command, replacing eth1 with whatever your active interface designation is:
```
sudo tcpdump -i eth1 ip6
```

Now surf to a URL that has been running slowly for you. Is there any output from tcpdump when you do this? And if so, what does the output look like?

If there's no output, that means that ipv6 isn't doing anything.

When I run that code I get this:

tt@tt-desktop:~$ sudo tcpdump -i eth1 ip6
[sudo] password for tt: 
tcpdump: SIOCGIFHWADDR: No such device

---

### Post by Brandon Williams on 2009-04-28
Note that I said "replacing eth1 with whatever your active interface designation".

You will have to figure out which of your interfaces has an IP address on it and specify that one in the tcpdump command line. It is most likely eth0, since eth1 doesn't work. But it could be something else. Use ifconfig to figure this out.

---

### Post by cybrsaylr on 2009-04-28
Thanks,
OK, Brandon when I run ifconfig in terminal this is the output:

tt@tt-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0a:cd:14:78:0f  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:cdff:fe14:780f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1005 errors:0 dropped:0 overruns:0 frame:0
          TX packets:781 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1070353 (1.0 MB)  TX bytes:197743 (197.7 KB)
          Interrupt:5 Base address:0x1000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



Howw do I change it to eth0  ?

---

### Post by cybrsaylr on 2009-04-28
> **Brandon Williams said:**
> Note that I said "replacing eth1 with whatever your active interface designation".

Just tried that. 
Ran this comand;
> sudo tcpdump -i eth0 ip6
and got this output:

tt@tt-desktop:~$ sudo tcpdump -i eth0 ip6
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes

---

### Post by cybrsaylr on 2009-04-28
FWIW,
Just did a little surfing since last post and it's still slow, no change yet...

---

### Post by Brandon Williams on 2009-04-28
Did anything show up in the tcpdump output when you were surfing? If not, then your system is not trying to use ipv6. It might still be trying to lookup ipv6 addresses, though, so try this:
```
sudo tcpdump -n -i eth0 dst port 53
```
Now do some more surfing. If the browser still seems slow, look for output from tcpdump that contains the string "AAAA?". If it is there, then your system is trying to look up ipv6 name records. If the string is not there, then ipv6 is not your issue.

---

### Post by cybrsaylr on 2009-04-28
Put in:
```
sudo tcpdump -n -i eth0 dst port 53
```

Did some surfing and there were several strings containing "AAAA?"
 for sites visited and browser is still slow.

---

### Post by Brandon Williams on 2009-04-28
Is it only when you're surfing that you see the AAAA? records? How about when you update your apt sources?

In firefox, enter about:config in the address bar, and then search for network.dns.disableIPv6. Double-click to change the setting to 'true'. That should fix delays when browsing. If you're experiencing slow connections in other apps, the other advice should have helped ... if it didn't I'm out of ideas.

---

### Post by cybrsaylr on 2009-04-28
9.04 is only slow when _surfing with Opera browser_, pages take to long to load compared to GG, HH and II.
Running apps, music, games etc, 9.04 runs normal with no lag.

Opera browser is my fav browser and that seems to be where the problem is, in Opera.
Just tried out Firefox and it's fast and normal and I had already disabled Ipv6 in the past the way you posted above.

I've had this Ipv6 issue with HH and II in the past. Because I use Opera I would disable IPv6 the way done in the OP. It worked like a charm and since it was done in Terminal Opera and Firefox were both sped up. That fix doesn't work with 9.04 however. 

It looks like I have to use FF until I find a way to speed up Opera browser which is where the lag is.

Anyone have any remedy for that?
Opera has been my fav browser for years because it's usually the fastest, faster than FF, except in this case with 9.04.

---

### Post by Brandon Williams on 2009-04-29
Ah-hah ... it's the Opera problem ...

As far as I know, the only way to fix this problem for Opera is to use a different DNS server. Try reconfiguring your networking to [use opendns]("https://www.opendns.com/start/ubuntu.php").

---

### Post by cybrsaylr on 2009-04-29
Brandon Williams,
Thanks! That did the trick!...):P

Opera is flying again in 9.04 like it was in previous Ubuntu versions.

Was using FF for the last day and like it, it's nice and all but my fav remains Opera which is again with that 'fix' you posted, faster than FF.

Thanks again.

PS:
What happened to ability to mark a thread/problem [SOLVED]?
Can't find that feature anymore and also we used to be able to 'Thank' posters who helped solve a problem in the past. Was that removed also?

Haven't used this forum for awhile.

---

### Post by cybrsaylr on 2009-04-29
Problem [SOLVED]

Opera is very fast again and 9.04 seems to be running fine.

---

### Post by stickman77 on 2009-04-30
Hi,

I've got the same issue here. I am experience performance issues in firefox and also on console with apt-get and ssh.

From what I have read this is a known issue that's been around since the start of this year or earlier where ipv6 has been compiled into the kernel in version 9.04 and it cant be switched off or disabled. The only way to disable it is to recompile your kernel by yourself.

I've read of people suggesting that users should replace their hardware or speak to the ISP as the ISP dns server is not supporting IPv6.

I don't believe that this is a reasonable solution. From the other forum thread's I've read if ipv6 was installed as a kernel module rather than compiled in to it then we would all have the option if we choose too turn it off. 

I see this as a workable solution for most people, but expecting all ISP's and hardware vendors to suddenly support ipv6 is just ridiculous.

As this issue has been around now for months and nothing has been done about it.. I'm thinking I'll do a clean install of a different distro which doesn't impose this restriction.

It's a shame as I like ubuntu.:(:(

My 2 cents hope it saves others some time reading through forums.

I'm not very technical so the stuff about the kernel is just my interpretation of what I've read so don't flame me.

---

### Post by cybrsaylr on 2009-04-30
stickman77,

You can disable Ipv6 in Firefox.

Here's a thread that deals with that:
[http://ubuntuforums.org/showthread.php?t=1014549](http://ubuntuforums.org/showthread.php?t=1014549)

It worked for me with FF but not with Opera.

---

### Post by stickman77 on 2009-04-30
Hi cybrsaylr,

Thanks for that... I've got loads of scripts and programs that I run from console that are also affected by this issue.

As an example. I've got one script that uses curl to check some things on a website.

Previously it would take around 2 seconds to execute... loading probably 5 different pages of content and extracting the data I'm after.

This was previous to the kernel changes. Now it takes just on 60 seconds to execute on the same hardware and internet connection.

That in my eyes is an enormous performance decrease. I've got adsl2+ which is about 20 mbit down and 8mbit up.... it feels like I'm on a dialup modem again.

This is not an issue with my hardware or internet connection. I've got a server running a different disto which still executes that code in 2 seconds. 

cheers

Stickman

---

### Post by cybrsaylr on 2009-04-30
I've read that IPv6 enabled, is a default setting that may cause problems, slow performance. When I disabled Ipv6, FF got much faster again.

---

### Post by stickman77 on 2009-04-30
yep your right... that is a work around for FF... but the rest of the issues still remain as with opera and any kind of console program or any other program that uses the internet/dns. They will all be slow.

---

### Post by cybrsaylr on 2009-04-30
Ubuntu versions prior to 9.04 were easy to fix for both FF and Opera in Terminal.

9.04 was much more complicated to fix for Opera. I had to reconfigure DNS as Brandon told me to do in Post #21 above.
After doing that, Opera is flying again faster than FF.
I like Opera the best, been using it for years.

---

### Post by stickman77 on 2009-04-30
yep that sounds right. I guess I was hopeful that this would get resolved and make it possible for people to have the choice of disabling ipv6.

I use my laptop on all different networks where those dns server may or may not be available.

I don't want to reconfigure my DNS every time i plug in somewhere new, should just get that info from DHCP which is the standard on most networks.

---

### Post by cybrsaylr on 2009-04-30
Gee, that's something to think about.
I only had to configure DNS on my desktop.

Still running 8.10 on my laptop.....wanted to see how 9.04 ran before putting it on the laptop to. I suppose I'll have the same issue with Opera on the laptop to when upgrading to 9.04.

Right now the laptop is running great with 8.10.

---

### Post by Brandon Williams on 2009-04-30
All of this makes me think that Opera is doing something different than the rest of the system where IPv6 is concerned. The standard library dns lookup routines have been modified for Jaunty in order to ensure that the system doesn't even try to perform IPv6 lookups unless there is a non-local IPv6 address on the system. If Opera is performing AAAA lookups, then it must be circumventing the new code somehow, perhaps by explicitly trying the IPv6 lookup itself instead of relying on the system to do it.

It might be possible to come up with an iptables rule to handle these DNS requests in a way that makes Opera think that they have failed. If you provide a tcpdump packet capture that shows the details of the DNS connection, I might be able to make a suggestion.

Also, you should consider opening and/or commenting on a bug in launchpad for this. It will only get changed/fixed if there is a launchpad bug.

---

### Post by cybrsaylr on 2009-05-01
> **Brandon Williams said:**
> It might be possible to come up with an iptables rule to handle these DNS requests in a way that makes Opera think that they have failed. If you provide a tcpdump packet capture that shows the details of the DNS connection, I might be able to make a suggestion.
Have no idea how to do that.

---

### Post by mrwoody on 2009-05-01
> **cybrsaylr said:**
> Brandon Williams,
Thanks! That did the trick!...):P

Opera is flying again in 9.04 like it was in previous Ubuntu versions.

Was using FF for the last day and like it, it's nice and all but my fav remains Opera which is again with that 'fix' you posted, faster than FF.

Thanks again.

PS:
What happened to ability to mark a thread/problem [SOLVED]?
Can't find that feature anymore and also we used to be able to 'Thank' posters who helped solve a problem in the past. Was that removed also?

Haven't used this forum for awhile.

This fix doesn't work for me. I cannot surf any page on opera as I get this error:

```
You tried to access the address http://www.cnn.com/, which is
currently unavailable. Please make sure that the Web address (URL) is
correctly spelt and punctuated, then try reloading the page.
Make sure your Internet connection is active and check whether other
applications that rely on the same connection are working.

```

---

### Post by Brandon Williams on 2009-05-01
> **stickman77 said:**
> yep your right... that is a work around for FF... but the rest of the issues still remain as with opera and any kind of console program or any other program that uses the internet/dns. They will all be slow.

It is supposed to be the case that the name lookup code in the standard library does not even try an IPv6 lookup (AAAA) if the only IPv6 addresses you have on your system are local. This appears to be the case for me with every app that I've tried. 

If you are seeing something different on your system, then I suggest opening a bug in launchpad. I remember seeing a bug related to this at some point, and the person the bug was assigned to was reluctant to change the IPv6 kernel config because the name lookup change should have solved the problem. If you have to reconfigure individual apps to get around the problem, then it seems that either the name lookup code is still broken or the kernel config will have to be changed after all.

FWIW ... you may be able to get curl to work for you in Jaunty by adding --ipv4 to your command line.

---

### Post by cybrsaylr on 2009-05-01
> **mrwoody said:**
> This fix doesn't work for me. I cannot surf any page on opera as I get this error:

```
You tried to access the address http://www.cnn.com/, which is
currently unavailable. Please make sure that the Web address (URL) is
correctly spelt and punctuated, then try reloading the page.
Make sure your Internet connection is active and check whether other
applications that rely on the same connection are working.

```
Whenever I got that error it was due to a loss of internet access.
It happened a week ago for half a day while service was down. All browsers didn't work till service was restored.

---

### Post by mrwoody on 2009-05-01
> **cybrsaylr said:**
> Whenever I got that error it was due to a loss of internet access.
It happened a week ago for half a day while service was down. All browsers didn't work till service was restored.

firefox is working but opera is not. So it is not my case.

---

### Post by Brandon Williams on 2009-05-01
mrwoody,

Does curl work if you explicitly tell it only to use IPv4 with the --ipv4 flag? Or are you still seeing AAAA requests in the tcpdump output, even with that flag?

---

### Post by cybrsaylr on 2009-05-01
> **mrwoody said:**
> firefox is working but opera is not. So it is not my case.
I've never had that happen. Whenever I got that message both browsers went down until internet service was restored.

---

### Post by mrwoody on 2009-05-05
> **Brandon Williams said:**
> mrwoody,

Does curl work if you explicitly tell it only to use IPv4 with the --ipv4 flag? Or are you still seeing AAAA requests in the tcpdump output, even with that flag?

Yes it seems that it works fine. Anything else I can try? 
I noticed that also the gnome applet "Weather Report 2.26.0" stopped working after I upgraded to Jaunty. So I guess there are some networks problems, but I am not exactly sure what (since firefox works fine).

---

### Post by Brandon Williams on 2009-05-06
MrWoody,

Just to verify, which of these three options from [this thread](http://ubuntuforums.org/showthread.php?t=1137127) have you tried?
[list]
[*]add the ipv6.disable=1 kernel boot parameter
[*]disable ipv6 using sysctl parameter: sudo sysctl -w net.ipv6.conf.all.disable_ipv6=1
[*]recompile kernel with IPv6 disabled
[/list]

I hope that recompiling the kernel is not required and that one of the other options will work for you, but if that is not the case, then I'm afraid that kernel recompilation is the only thing left that I can think to recommend, given your operational requirements.

Unfortunately, I don't have the problem you're having on either my lpia install or my amd64 install. Neither one is attempting to send any ipv6 traffic, nor is either one sending AAAA dns requests. I've tried a variety of programs and I simply can't find one that behaves badly, so I can't test any of the proposed solutions to see if they will solve your problem. I keep hoping that someone who has actually experienced and fixed this problem will comment .... anyone?

There are a small number of ipv6 related bugs in launchpad for Jaunty. You should consider commenting on one or more of them to help raise the priority.

---

### Post by mrwoody on 2009-05-07
> **Brandon Williams said:**
> MrWoody,

Just to verify, which of these three options from [this thread](http://ubuntuforums.org/showthread.php?t=1137127) have you tried?
[list]
[*]add the ipv6.disable=1 kernel boot parameter
[*]disable ipv6 using sysctl parameter: sudo sysctl -w net.ipv6.conf.all.disable_ipv6=1
[*]recompile kernel with IPv6 disabled
[/list]

I hope that recompiling the kernel is not required and that one of the other options will work for you, but if that is not the case, then I'm afraid that kernel recompilation is the only thing left that I can think to recommend, given your operational requirements.

Unfortunately, I don't have the problem you're having on either my lpia install or my amd64 install. Neither one is attempting to send any ipv6 traffic, nor is either one sending AAAA dns requests. I've tried a variety of programs and I simply can't find one that behaves badly, so I can't test any of the proposed solutions to see if they will solve your problem. I keep hoping that someone who has actually experienced and fixed this problem will comment .... anyone?

There are a small number of ipv6 related bugs in launchpad for Jaunty. You should consider commenting on one or more of them to help raise the priority.

Thanks for your message. I tried the first two solution, but didn't work. I will try and compile the kernel when I have a chance to do so. But now I am not really very sure that it really depends on ipv6. We'll see. 
I get this in dmesg: 
```

[   44.448015] eth0: no IPv6 routers present

```

---

### Post by Brandon Williams on 2009-05-07
Before going through the trouble of a kernel recompile, I suggest that you verify that ipv6 is really the problem. This should be simply enough to do with tcpdump.
```
$ sudo tcpdump -nvvv -i *eth0* 'ip6 or port 53'
```
Replace *eth0* with the name of your primary internet device.

If you see any output with IPv6 addresses or you see the string "AAAA?" in the output, then you might be able to correct the problem by disabling ipv6, but if you don't see any indication that it's actually trying to send ipv6 packets or ipv6 nameserver requests, I would be surprised if disabling ipv6 actually worked.

One other thing occurs to me, and it probably isn't related, but ... I always deinstall avahi-autoipd, because I don't use any zeroconf-type functionality. It's always possible that the interface activity of avahi-autoipd is somehow involved. Again, I doubt it, but it wouldn't hurt to experiment.

And one final thing ... You might try commenting out all of the ipv6 entries in /etc/hosts. I doubt this will do anything either, but it might. I'm just trying to think of the things that a program might do to figure out whether it should be attempting anything related to ipv6.

---

### Post by mrwoody on 2009-05-07
> **Brandon Williams said:**
> Before going through the trouble of a kernel recompile, I suggest that you verify that ipv6 is really the problem. This should be simply enough to do with tcpdump.
```
$ sudo tcpdump -nvvv -i *eth0* 'ip6 or port 53'
```
Replace *eth0* with the name of your primary internet device.



Thanks again for your help. I don't see anything related with ipv6, so I agree with you, this shouldn't be the error.  I am not sure if it helps, but when I try to use opera I get this: 

```
 16:40:55.044467 IP (tos 0x0, ttl 63, id 21281, offset 0, flags [DF], proto UDP (17), length 142) 155.198.142.7.53 > 155.198.192.116.55654: 34922 q: A? www.economist.com. 1/3/0 www.economist.com. A[|domain] 
```

---

### Post by Brandon Williams on 2009-05-07
Is that all you see? Just the one line? There should be at least two, one request with '155.198.192.116.55654 > 155.198.142.7.53' and one response with '155.198.142.7.53 > 155.198.192.116.55654'. I'm interested to see how far apart the request and the response are.

When go to [www.economist.com](www.economist.com) in firefox, it actually takes about 5 seconds for the page to start loading, because the first request times out. But there is not ipv6 related activity.

---

### Post by mrwoody on 2009-05-08
> **Brandon Williams said:**
> Is that all you see? Just the one line? There should be at least two, one request with '155.198.192.116.55654 > 155.198.142.7.53' and one response with '155.198.142.7.53 > 155.198.192.116.55654'. I'm interested to see how far apart the request and the response are.

When go to [www.economist.com](www.economist.com) in firefox, it actually takes about 5 seconds for the page to start loading, because the first request times out. But there is not ipv6 related activity.

Hard to believe but this morning opera started to work ( I am not sure if I upgraded something in the meanwhile, and someone solved the bug). The gnome applet doesn't work yet, but I can leave without. 
Thanks for your help!

---

### Post by Brandon Williams on 2009-05-08
Out of curiosity, do you have the jaunty-proposed repository enabled? There is a kernel update there that, among other things, is supposed to support the ipv6.disable kernel boot parameter and/or the net.ipv6.conf.all.disable_ipv6 sysctl setting. Do you still have an ipv6 addresses on your interface?

---

### Post by mrwoody on 2009-05-08
> **Brandon Williams said:**
> Out of curiosity, do you have the jaunty-proposed repository enabled? There is a kernel update there that, among other things, is supposed to support the ipv6.disable kernel boot parameter and/or the net.ipv6.conf.all.disable_ipv6 sysctl setting. Do you still have an ipv6 addresses on your interface?

sorry for the ignorance, but how do i check that? is it this one? 

```
 inet6 addr: fe80::221:5aff:fee8:5b74/64 Scope:Link 
```

Also, is there a way to check what are the last ubuntu packages which were upgraded on my machine? 

Thanks again!

---

### Post by Brandon Williams on 2009-05-08
> **mrwoody said:**
> sorry for the ignorance, but how do i check that? is it this one? 

```
 inet6 addr: fe80::221:5aff:fee8:5b74/64 Scope:Link 
```

Also, is there a way to check what are the last ubuntu packages which were upgraded on my machine? 

Thanks again!

Yes, that is an ipv6 address ... so the sudden self-correction appears to have nothing to do with ipv6 magically getting turned off.

If you want to see what the latest updates were, you can check /var/log/aptitude and /var/log/apt/term.log.

---

### Post by cybrsaylr on 2009-05-11
> **cybrsaylr said:**
> Brandon Williams,
Thanks! That did the trick!...):P

Opera is flying again in 9.04 like it was in previous Ubuntu versions.

Was using FF for the last day and like it, it's nice and all but my fav remains Opera which is again with that 'fix' you posted, faster than FF.
Well, back again.

Upgraded my Toshiba AMD Laptop from 8.10 32bit to 9.04 64bit Jaunty and Opera is slow again.
Tried a couple fixs in this thread with no luck. Firefox is fast but Opera crawls on 64bit. Brandon I tried your fix in Post #21 but it didn't help but then that was for 'wired' and I'm using 'wireless' now. Didn't want to try it with wireless for fear of knocking out my wireless connection which is running great.

Any idea how to get Opera flying again on 9.04 64bit JJ?

---

### Post by cybrsaylr on 2009-05-12
Just got my JJ CD from Shipit, assume it's the 32bit version of 9.04.

Seriously thinking about installing it to see if it will fix the lag issue with Opera browser.

Out of curiosity I did try the fix from post #21 on my laptop and it did knock out laptop wireless. I then reinstalled 64bit 9.04 and all was good again with wireless but Opera is still slow.

32bit 9.04 runs faster on my old desktop PC than 64bit 9.04 is running on my new Toshiba AMD laptop.

---

### Post by Brandon Williams on 2009-05-12
There's no reason not to try using opendns to see if it resolves your opera issue on the other system. You can always set it back the way that it was if using opendns causes other issues for you.

The decision to use opendns has absolutely no bearing on whether the connection is wired or wireless. The communication medium is a level or two below dns in the network stack.

---

### Post by cybrsaylr on 2009-05-12
> **Brandon Williams said:**
> There's no reason not to try using opendns to see if it resolves your opera issue on the other system. You can always set it back the way that it was if using opendns causes other issues for you.

OK Brandon Williams,
Tried that opendns fix again.
FF is fast but Opera still acts screwy.
Opera lags when cliking on a site but then once in, it picks up some speed on some but not all sites visited. FF runs/loads quicky on generally all sites right now on 64bit 9.04.

However both FF and Opera ran/loaded faster overall on 32bit 8.10 on this same Toshiba AMD laptop with Opera easily out performing FF there.

---

