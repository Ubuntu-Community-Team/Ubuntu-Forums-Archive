---
title: "Connection doesnt work after upgrade"
date: 2009-04-26
forum: General Help
---

### Post by AFUNA on 2009-04-26
Hello
After I upgraded my ubuntu to 9.04 using Upgrade manager my connection stopped working
yes I can see the icon shows that am connected but can do anything on the internet
firefox shows that I have no connection so I failed connecting to websites .. etc
so Would you help me please ..
Thanks and have a nice day ..

---

### Post by Iowan on 2009-04-27
Wired/wireless?
Static/DHCP IP address?
Does *ifconfig* show a good address (preferably NOT avahi's 169.254.X.X)?
If valid address, can machine ping gateway (modem, router, etc)?

---

### Post by AFUNA on 2009-05-01
- Wired ..
- DHCP IP address
- ya
- I quite didnt get this question :oops:

would u please tell me is there any troubleshooting or something I can fix it with
or advanced options cos the options that the normal options can show more choices to deal with like windows
ps: am purely 100$ linux newbie so I hope you gimme any advices step by step :oops:

---

### Post by Butthead on 2009-05-01
Same thing happened to me.

Run the "Recovery" menu option in Grub, and have it fix any broken packages.

---

### Post by Butthead on 2009-05-01
Mine stopped working again too.  Seems that's not a fix. :cry:

---

### Post by AFUNA on 2009-05-08
up !!

---

### Post by Peter09 on 2009-05-08
Can you post the output of the commands
```
ifconfig
```

and

```
route
```

---

### Post by AFUNA on 2009-05-08
About the first command "ifconfig"
```
eth0      Link encap:Ethernet  HWaddr 00:1d:92:de:f9:f7  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:92ff:fede:f9f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:300 errors:0 dropped:0 overruns:0 frame:0
          TX packets:215 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26428 (26.4 KB)  TX bytes:17096 (17.0 KB)
          Interrupt:251 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```
and about the second command "route"
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
```
I hope it get fixed soon I cant wait to get back to my lovely ubuntu

---

### Post by Peter09 on 2009-05-08
Well you are connected, but I think you have no gateway configured. How do you connect to the internet, through a router or through a modem?

---

### Post by AFUNA on 2009-05-08
a router ..

---

### Post by Peter09 on 2009-05-08
Are you using DHCP or a static ip? If static, try enabling DHCP and see if things work.

---

### Post by AFUNA on 2009-05-08
am using a DHCP ..
I forgot to attach the pic of my connectivity test
so I attached it here ..

---

### Post by Peter09 on 2009-05-08
Ok - I presume this is a page from your router setup, not a modem setup. The router looks ok, but your PC does not have the gateway configured.

Try right clicking on the network icon and editing the network. For DHCP you should have no other configuration in the Boxes.

---

### Post by AFUNA on 2009-05-08
It is already has no other configuration in the Boxes.

---

### Post by Peter09 on 2009-05-08
Check /etc/network/interfaces.

The file should not exist or be empty in Jaunty.

EDIT:
Sorry thats not right it should look like this:


> auto lo
iface lo inet loopback

---

### Post by AFUNA on 2009-05-08
It isnt exist ..
edit // wait till I check after the edit

---

### Post by Peter09 on 2009-05-08
Don't worry if it does not exist - its does not exist on some of my installations as well.

---

### Post by Peter09 on 2009-05-08
Try the following as a temporary setup

```

**route add default gw {IP-ADDRESS} {INTERFACE-NAME}**

```
where

[LIST]
[*]IP-ADDRESS: Specify router IP address
[*]INTERFACE-NAME: Specify interface name such as eth0
[/LIST]
Then try your connection again

---

### Post by AFUNA on 2009-05-08
it keeps saying unknown host :(

---

### Post by Peter09 on 2009-05-08
Sounds like you have the wrong IP address for your router, what IP address are you using?

---

### Post by AFUNA on 2009-05-08
IP address: 192.168.x.x
Default Gateway: 192.168.x.xxx

---

### Post by Peter09 on 2009-05-08
This is an internal IP schema so there is no need for secrecy as it should not be visible on the otherside of your router.

Normally the gateway will be something like

192.168.0.1

Here is my route output.

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

Note the bottom line which is specifying the gateway - yours is missing.

---

### Post by AFUNA on 2009-05-08
I dunno about publishing my info to the public so I emailed it to u ;)

---

### Post by Peter09 on 2009-05-08
No email messages yet.

Can you try some other checks to test that your router IP is what you think, look in the router set up and check what the internal IP address is.

---

### Post by AFUNA on 2009-05-08
check again now I sent you all my connection info
Thanks for the great assitance ..

---

### Post by Peter09 on 2009-05-08
Got your email.

According to this your default gateway IP is the one opposite the text Default Gateway (unsurprisingly). Is this the one that you are using.

---

### Post by AFUNA on 2009-05-08
yup ..

---

### Post by Peter09 on 2009-05-08
Do you get a response from

```
ping <ip of gateway>
```

---

### Post by AFUNA on 2009-05-08
it keeps saying
```
bash: syntax error near unexpected token `newline'
```

---

### Post by Peter09 on 2009-05-08
Ok you do not need the angle brackets in the command, they are commonly used to denote something that you must change to your own configuration. In this case your ip number.

So login would look like
:
username: <your user name>
password: <your password>

---

### Post by AFUNA on 2009-05-08
ok it pings normally and I get a response.

---

### Post by Peter09 on 2009-05-08
Can you try the route command to set the gateway again, make sure you do not use the brackets. Can you post the route command that you used.

If it works can you post the output of
```
route
```

Also try turning off your wireless connection.

You may need to restart networking with this command after each test.

```
sudo /etc/init.d/networking restart
```

also check

```
ping www.google.com
```

I think you are having to boot between windows and Ubuntu so I am putting a lot of tests together to shorten the cycle.

---

### Post by AFUNA on 2009-05-08
still doesnt work
when I try to ping google it keeps saying
```
connect: Network is unreachable

```even after restarting ..

---

### Post by Peter09 on 2009-05-08
But what about the route command


 	Code:
 	**route add default gw {IP-ADDRESS} {INTERFACE-NAME}** 
where

[LIST]
[*]IP-ADDRESS: Specify router IP address
[*]INTERFACE-NAME: Specify interface name such as eth0
[/LIST]
We need to get this command to work!

---

### Post by AFUNA on 2009-05-08
Cant make it work :(
all my attempts failed ..
[SIZE="1"]*(started to give up!)*[/SIZE]

---

### Post by Peter09 on 2009-05-09
Can you post the response to the command

```
**route add default gw {IP-ADDRESS} {INTERFACE-NAME}**
```

and (important) show me the command you issued (xx out the bits you want to remain private.

---

### Post by AFUNA on 2009-05-09
The results were ..
> **AFUNA said:**
> it keeps saying unknown host :(

---

### Post by Peter09 on 2009-05-09
I would really like to see what text you typed in, also are you putting sudo in front of the command - I should have been more detailed on that.

```

 	**sudo route add default gw {IP-ADDRESS} {INTERFACE-NAME}** 
```

---

### Post by AFUNA on 2009-05-09
Here u are a screenshot ..
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=112999&stc=1&d=1241858378[/IMG]


even that this is the same default gateway am using on windows ..

---

### Post by Peter09 on 2009-05-09
:) The curly brackets are not needed - they are doing the same role as the angle brackets were earlier in our conversation.

Also the interface is eth0 (no auto)

Can we do the command again

---

### Post by AFUNA on 2009-05-09
I made it but didnt get any connection :(


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=113000&stc=1&d=1241860051[/IMG]

---

### Post by Peter09 on 2009-05-09
Its not auto eth0 - just eth0

the command should be

```
 sudo route add default gw 192.168.xx.xx eth0

```

---

### Post by AFUNA on 2009-05-09
ya but the connection is named with auto eth0
thats why I keep writting it .. should I ignore it and write it eth0 ?

---

### Post by Peter09 on 2009-05-09
Just eth0 - when you see the auto it just means the interface will connect automatically.

---

### Post by AFUNA on 2009-05-09
lol guess what am back :D
and this post is from my lovely ubuntu
Back to the Original :guitar:
thanks for the great help
is there anything I can do ..?

---

### Post by Peter09 on 2009-05-09
Check the route sticks with a reboot and if you have a wireless connection then check that works as well.

The puzzle is that it should set the gateway automatically .... perhaps your router does not advertise as a gateway?

---

### Post by Peter09 on 2009-05-09
Any way welcome back .....

---

### Post by AFUNA on 2009-05-09
after the reboot I have to make the same steps again
ps: am not a wireless connection

---

### Post by Peter09 on 2009-05-09
Here you go - follow this link and add the route you need.

[http://www.ubuntugeek.com/howto-add-permanent-static-routes-in-ubuntu.html](http://www.ubuntugeek.com/howto-add-permanent-static-routes-in-ubuntu.html)

---

### Post by AFUNA on 2009-05-09
I dunno but cant make the second step
cant figure out the commands
```
    up route add [-net|-host] <host/net>/<mask> gw <host/IP> dev <Interface>
```
specially [-net|-host] <host/net>/<mask>

---

### Post by Peter09 on 2009-05-10
Try in /etc/network/interfaces

auto eth0
        up route add default gw <gateway IP>


then restart with

```
/etc/init.d/networking restart
```

---

### Post by AFUNA on 2009-05-15
Unfortunately ..
```
afuna@afuna-desktop:~$ sudo nano /etc/network/interfaces
afuna@afuna-desktop:~$ /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          /etc/network/interfaces:2: misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:2: misplaced option
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                         [[COLOR="DarkRed"]fail[/COLOR]]
afuna@afuna-desktop:~$ 

```

---

### Post by Peter09 on 2009-05-15
Can you show the contents your /etc/interfaces file

---

### Post by AFUNA on 2009-05-15
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=113854&stc=1&d=1242369498[/IMG]

---

### Post by Peter09 on 2009-05-15
OK try changing the up etc line to just

> gateway  192.168.1.254

---

### Post by AFUNA on 2009-05-15
Still the same fail result :(

---

### Post by Peter09 on 2009-05-15
Just realised 
>  /etc/init.d/networking restart

need sudo in front

```
 sudo /etc/init.d/networking restart

```

---

### Post by AFUNA on 2009-05-21
yesterday I did an update to the system and I rebooted the system and didnt need to set my gateway manually so I guess the problem is solved now
special thanks to Peter09
you was a great helper I hope I can repay you someday :oops:

---

