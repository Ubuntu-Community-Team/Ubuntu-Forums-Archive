---
title: "LTSP5: Installed Firefox as a local-app, how do I get Flash too?"
date: 2009-01-15
forum: General Help
---

### Post by tawmas on 2009-01-15
Hello,

I'm experimenting with LTSP5. For performance reasons, I need to run Firefox (complete with Flash support) in the thin clients, so I was looking and local-applications.

Unfortunately, documentation is silent on this point, and I couldn't find any useful guide by googling -- just a few blog posts telling it worked for the posters, including a post by the Edubuntu LTSP developers themselves, but nobody is telling how they did that, again including the Edubuntu LTSP developers. :-(

I solved half of the puzzle, and it was quite easy: I do have a working Firefox installed as a local-application (this is easy to do, see below for a quick recipe), but I couldn't get Flash.

This is what works:

1) Make sure you can reach the Internet from the thin clients themselves. For this, you will need to provide NAT for the thin clients. I just followed the [Thin Client How-To NAT]("https://wiki.ubuntu.com/ThinClientHowtoNAT") guide from the wiki and was good to go.

2) Install Firefox inside the chroot and rebuild the image

```
sudo chroot /opt/ltsp/i386
sudo apt-get update
sudo apt-get install firefox
sudo xulrunner-1.9 --register-global
exit
sudo ltsp-update-image
```

The 4th line is to work around a known bug. Google for "Could not find compatible GRE between version 1.9.0.1 and 1.9.0.*." if you're curious! :-)

3) Reboot your clients. At this point, you can launch Firefox with

```
ltsp-localapps firefox
```


Once I got this to work, I thought that getting Flash on top of that would be a piece of cake, so I went back into the chroot, installed flashplugin-nonfree and updated the image, but after another reboot of the clients there was no Flash plugin.

I then tried to install ubuntu-restricted-extras too, which again completed with no error messages, updated the image and rebooted the thin clients, but still no Flash plugin. Indeed, about : plugins shows no plugin installed (except the default plugin).


To further clarify, I have ubuntu-restricted-extras installed on the LTSP server. Firefox instances started the usual way do have the flash plugin and everything is working. I also have ubuntu-restricted-extras installed inside the LTSP chroot, but Firefox instances started as local-applications do not have the flash plugin available.

I could really use some suggestion as to how further investigate the matter or what to try next.

---

### Post by wesblake on 2009-04-20
Perhaps you can at least help me to get the Firefox running locally at all since you had luck!
I followed your guide above, after following a few others I found saying basically the same thing, and I get no connection.
Clarification:
On a client, I can start firefox normally and get an internet connection. I can also ping site from a terminal on the client.
However, if I open firefox as a local app using ltsp-localapps, firefox opens, but seems to have no connection still, just gives the "page not found" error for everything you try to surf to.
Any ideas? Thanks.

---

### Post by tawmas on 2009-04-21
This looks like one (or many) of these possible problems:

1) your thin clients cannot resolve domain names
2) your thin clients cannot properly route packets
3) your router (tipically the LTSP server) won't route packets from the clients

All of this is covered in the [Thin Client Howto NAT]("https://wiki.ubuntu.com/ThinClientHowtoNAT") I linked above.

To troubleshoot the problems, you can run xterm on the thin clients as a local application with the command below:

```
ltsp-localapp xterm
```

From there, you can do things like
```
ping www.ubuntu.com
route -n
cat /etc/resolv.conf
```
and so on to verify the network settings on the clients.

If you need further help, please post here the output of those commands as well as a few details about your network (IP of the LTSP server, IP of the gateway, name or IP of your DNS server(s)).

---

### Post by minholi on 2009-04-27
> **tawmas said:**
> 
If you need further help, please post here the output of those commands as well as a few details about your network (IP of the LTSP server, IP of the gateway, name or IP of your DNS server(s)).

Hi tawmas,

I just installed a Ubuntu 9.04 LTSP server and running 'ltsp-localapps xterm' I saw that /etc/resolv.conf is unreadable, look:

```
root@ltsp20:/etc# ls -la resolv.conf
---------- 1 root root 0 2009-04-27 08:31 resolv.conf
```

Is there a fix for this? Looking at launchpad I found this bug:

[https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/347957](https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/347957)

It's just what happens here.

---

### Post by wesblake on 2009-05-06
Minholi - I found this for your problem before. A script you can create and run on ltsp bootup that fixes your problem:
[https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/348305](https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/348305)

I myself am still having issues, I've actually upgraded the ltsp server/images to 9.04, so I am not having the issue Minholi is. I sort of figured things out and perhaps someone can help me find a work around.
Still no internet for clients. However, I found out how to get internet.
If I look at resolv.conf on the server, it has the isp given dns servers, and internet on their works fine. If I look at resolv.conf on the clients, it's the same and no internet. If I modify resolv.conf on the clients so the dns server is the ip of the ltsp server, internet works for locally run firefox! However, when I edited resolv.conf on the client it actually edited resolv.conf on the server, so it appears that /opt/ltsp/i386/etc/resolv.conf is never used? I've tried editing that file and updating the image, setting SEARCH_DOMAIN and DNS_SERVER in lts.conf, no matter what, the clients actually use the server's resolv.conf. How do I get the clients to use the resolv.conf from the image or chroot so it can be different from the servers resolv.conf?
Thanks for any help. I suppose worse case, I can go ahead and edit the server's resolv.conf so the clients work and then just edit it back when I need to do updates on the server.

---

### Post by wesblake on 2009-05-06
Scratch the last post. I was wrong, it just appears that the internet works off an on on the clients, it's simply not working reliably and it happened to start working again right after modifying resolv.conf which made me think that was the issue.

I'll post what I can below, I really need to solv this if anyone can help. Thanks:

ping [www.ubuntu.com](www.ubuntu.com)
ping: unknown host [www.ubuntu.com](www.ubuntu.com)

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG      0    0        0 eth0

cat /etc/resolv.conf
cat: /etc/resolv.conf: Input/output error

/etc/ltsp/dhcpd.conf contents:
authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
    range 192.168.0.20 192.168.0.250;
    option domain-name "*";
    option domain-name-servers 192.168.1.168;
    option broadcast-address 192.168.0.255;
    option routers 192.168.0.1;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}

/var/lib/tftpboot/ltsp/i386/lts.conf contents:
[default]
LOCALDEV=True
SOUND=True
LOCAL_APPS_MENU=True

If I can show anything else that might help, please let me know. Thanks.

---

### Post by zaltabar on 2009-07-08
After some tweaking, googling and pondering I now have Firefox up and running as a local app.

What I've done so far:

[https://wiki.ubuntu.com/ThinClientHowtoNAT](https://wiki.ubuntu.com/ThinClientHowtoNAT)

----------------------------------
Installed firefox, flash and java:
----------------------------------
sudo chroot /opt/ltsp/i386
apt-get install firefox
apt-get install ubuntu-restricted-extras
ln -s /usr/lib/adobe-flashplugin/libflashplayer.so /usr/lib/firefox-3.0.11/plugins/libflashplayer.so 

exit

-----------------------------------------
Edit /var/lib/tftboot/ltsp/i386/lts.conf:
-----------------------------------------
SEARCH_DOMAIN = thin.local
DNS_SERVER = 208.67.222.222

RCFILE_01 = /etc/init.d/chmod-resolv.sh

-----------------------------------------
Create /opt/ltsp/i386/etc/init.d/chmod-resolv.sh:
---------------------------------------------------
#!/bin/sh
chmod 644 /etc/resolv.conf

-----------------------------------------
Edit /etc/ltsp/dhcpd.conf:
-----------------------------------------
option domain-name "thin.local"
option domain-name-servers 208.67.222.222,208.67.220.220
option routers 192.168.0.254

-------------
Rebuild image
-------------
sudo ltsp-update-image

At least I think that's all I've done so far.
The problem: Flash is extremely slow. It finally works somehow, but it's not something I could use. And using Flash was the whole point...

Ideas?

---

### Post by tawmas on 2009-07-08
> **zaltabar said:**
> After some tweaking, googling and pondering I now have Firefox up and running as a local app.

What I've done so far:

Ouch! That looks tremendously more complicated than what I had to do to get it to work! :-( I'm happy to know that you managed to do that!

> **zaltabar said:**
> At least I think that's all I've done so far.
The problem: Flash is extremely slow. It finally works somehow, but it's not something I could use. And using Flash was the whole point...

Ideas?

First and foremost, what kind of CPU*do your thin clients have? And even more important, how much RAM? Flash is not easy on either, especially Flash video.

---

### Post by zaltabar on 2009-07-09
Thanks for your quick reply!

I'm pretty sure I overcomplicated things ;)

Running Firefox as a local application was no problem. I had to set the permissions on /etc/resolv.conf to make the thin client resolv domain names. I think this is the same bug as "minholi" mentioned.

The thin client in my lab is a "Dell Optiplex GX240" (Pentium 4, 512MB RAM) so it should be able to run flash without breaking a sweat. My plan was to use lts.conf to have the "fatter" clients running Firefox locally and the "weaker" clients running it on the server. 

As you can see I've installed "ubuntu-restricted-extras" in the LTSP chroot (as well as on the server) but I still had to "cheat" with the symbolic link (ln -s /usr/lib/adobe-flashplugin/libflashplayer.so /usr/lib/firefox-3.0.11/plugins/libflashplayer.so).

---

### Post by tawmas on 2009-07-09
Yes, that should be enough... I don't know what more to suggest, then... Sorry!

---

### Post by zaltabar on 2009-07-11
I still have a couple of weeks until the students return from summer vacation to figure out where the bottle neck is. This thread gave me some nice pointers to get me in the right direction. So thank you and I'll try to remember to put up a post here when (or if) I get things up and running the way they should.

---

### Post by zaltabar on 2009-07-20
It works!

Turns out /sys and /proc was not mounted (in LTSP chroot).
So I mounted those two, did a "sudo apt-get update" and "upgrade". Voila!


Probably a silly mistake...and those are often the ones hard to spot.

---

### Post by AlexanderDGreat on 2009-12-09
Hi zaltabar, thanks for the post, it helped me a lot.

However, how can I launch Firefox as a local app without having to type ltsp-localapps firefox everytime? I already followed this guide [https://help.ubuntu.com/community/UbuntuLTSP/LTSPLocalAppsJaunty](https://help.ubuntu.com/community/UbuntuLTSP/LTSPLocalAppsJaunty) but it won't launch locally without typing the ltsp-localapps command.

PS In your post, so how do you mount /sys /proc in the LTSP chroot? Isn't that automatic when you boot your thin client?

---

### Post by tentwelveeight on 2009-12-10
Hi, I had the same problem once, but every other time I've done it the local apps worked fine. I've written a howto that I think is a bit easier to follow than the one you used, although I borrow heavily from the original. Here's mine:
[URL="https://help.ubuntu.com/community/UbuntuLTSP/LTSPLocalAppsFirefox"]https://help.ubuntu.com/community/UbuntuLTSP/LTSPLocalAppsFirefox
[/URL]
I would suspect your problem lies in your lts.conf but I'm not sure. Also, if you can stomach it, local apps is much easier with karmic. regards -joe

---

