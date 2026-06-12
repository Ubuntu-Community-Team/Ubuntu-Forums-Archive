---
title: "How do you create a home network?"
date: 2009-05-03
forum: General Help
---

### Post by szaemon on 2009-05-03
This is a very basic request, if the information is already here please point me in the right direction. I would like to know how to make two computers connect through a router. I have never done any kind of networking before and I'm not sure exactly what information I need or where to find it in my computer. I have searched this forum and the web. but the information I keep finding seems to be explaining more advanced aspects of networking or how to trouble shoot, assumimg people already know the basics. I believe this is the right section of the Ubuntu forum:

Wired (LAN)

DHCP connections (where settings are concfigured by your router) are automatically configured. Wired network connections are selected as default when connected.
DHCP Connections

Most routers use DHCP to allocate IP addresses.

   1.

      Click the NetworkManager icon in the system notification area.
   2.

      Under Wired Network click the Radio Button next to the network you want to connect to.

Static Connections

If you don't use DHCP then you can configure a static connection.

   1.

      Right click the NetworkManager icon in the system notification area.
   2.

      Click Edit Connections.
   3.

      Click the Wired tab.
   4.

      Select the connection and click Edit.
   5.

      Click the IPv4 tab.
   6.

      Choose Manual from the Method drop down.
   7.

      Enter your details and click OK.
   8.

      Click Close.

However, I don't see anything about radio channels under Wired Network. I see this: Auto ethO then VPN Connections. But perhaps I don't use DHCP (I don't know) Looking at the second section< I can follow it up to step 7. Enter your details and click OK. I do not know what these details are or where to locate them.

I have 2 computers running Ubuntu 9.04, a router: RT-200NE, and an ADSL Modem: GE-PON <M>A GE-PON-ONU<1><2>. Both of my computers have LAN cables connected to the router. And they both connect to the internet. This should be a very simple task, I just don't know where to start. 
Thanks in advance for any help that is offered.

---

### Post by szaemon on 2009-05-03
Someone, please. Just tell me where I can find clear easy to follow instructions.

---

### Post by CatKiller on 2009-05-03
A [radio button]("http://en.wikipedia.org/wiki/Radio_button") is just a graphical element.

DHCP is a way of automatically assigning IP addresses. This will be handled by the router, and is probably enabled by default. You'll need to configure your router if you want to change this. Most routers are able to be configured using a web browser. Your router documentation will tell you how to do this.

You can find out what the IP address of each of the computers is by running *ifconfig* on each of them. If you want your computers to always have the same address no matter which one of them connects to the router first, then you need to set up static IP addresses for each of them. Some routers will let you do this based on the MAC address of each of the network cards, or you can set a static IP address in Ubuntu.

How you proceed after you know the IP address of each of the computers depends on what you're trying to achieve; SSH, file sharing, remote desktop, shared devices, that sort of thing.

---

### Post by szaemon on 2009-05-03
Cat Killer, thank you for your explanation. I now have the IP addresses of both computers. My router(RT-200NE) documentation and customer service call center is all in Japanese, they just tell me it can't be done and hang up. There are some deffinate roadblocks to living in Japan...

What I am trying to do is give each of my computers and only "my" computers complete and total access to each other through my router... or as close to that as possible. Is that a difficult task?

Any support you or anybody else could give me would be appreciated.
Thanks.

---

### Post by TideMan on 2009-05-04
The way I've done this is to make one of my machines a server and the other a client.
You need to install openssh-server on one machine and openssh-client on the other using the Synaptic Package Manager
Then on the server, you set it going:
ssh localhost
and on the client, you login using:
ssh 192.168.1.104
or whatever the IP address of the server is.
You will be asked for the username and password of your account on the server.
Now you have access to everything on the server.

Once you've got this working, there are many things you can do to make life easy for you.......

---

### Post by lisati on 2009-05-04
There are a number of ways of setting up a home network. My own network, which includes a mixture of assorted flavours of Windows and Ubuntu, and a couple of routers. I used the tutorial at [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) as the basis for configuring the Ubuntu parts of the network. This tutorial also includes some ideas on configuring Windows as well.The other machines on the network can (usually) be seen on Ubuntu via "Places->Network". On XP it's "My network places"->View workgrop computers, and on Vista it's on "Network".

---

### Post by sgosnell on 2009-05-04
Install samba on both computers, then enable sharing on both for the folders you want to be able to access from the other computer.  The easy way to enable sharing is to right-click on the folder, select Properties, then go to the Sharing tab and set the permissions you want.  You should then be able to access those folders through Nautilus, through Places, Network.

---

### Post by mb_webguy on 2009-05-04
If you have two or more computers connected to a router, you already have a home network.  The question is now how you want to use it.  If you want to share files between the computers, Samba is probably the most painless method, as sgosnell mentioned above.

---

### Post by szaemon on 2009-05-05
I just want to say thanks to you all for posting in response to such a basic question. I feel quite at odds with this whole computerised world we live in and it's helpful people like you folks who give me hope that I may yet survive this Modern Age.

Thank You.

---

### Post by szaemon on 2009-05-05
I'm back again with a few more questions about how to set this up. Thanks again for the advice, but I ran into a few roadblocks.

TideMan, I downloaded openssh-server and openssh-client, but I can't find where they are to configure or use them. They're not listed under applications>internet or applications>accessories. I can't find them under places or system>administration either. I don't know wjat to do with them.

mb_webguy,sgosnell and lisati, synaptic says that Samba is already installed. I have the same problem as with openssh. Where is it? My guess is that both of these install in some way that is not obvious to the untrained eye. I guess I'm looking in the wrong place. I'll keep checking.  Well anyway,I checked the tutorial link that lisati put up....WoW! Is that considered painless these days? Whew!...  If I go through the terminal as the tutorial suggests, I could just start where samba is already installed. I got up to the box that says code. And then I got stuck. There's a need for a lot of details in there that explained nor are they listed in the Network Manager's Connection Information Box. The Hostname ( iguess) can be anything I chose but,server string??? it's left blank in the tutorial, worgroup? How do I find my Workgroup in Ubuntu?, Do I have a static IP address? I don't know. I probably should know, but I do not. And so much more... the list goes on and on. The author, Stormbringer, says this is a more detailed guide and true it is, but this layman has no understanding of those details.  Where do I get all this information? And how do I get understanding of it all? What does it mean to "uncomment" something anywas. So much I need to learn.

Thanks again for any help offered.

---

### Post by netwarriorwy on 2009-05-05
Hi Szaemon!

If you wanna know where the applications or packages you've just installed you can do this:

> 
System->Administration->Synaptic Package Manager
Quick Search for the package you want e.g.: samba
Select it doing a single click
Go to the menu Package->Properties->Installed Files (tab)


There you can see all the places the files from the package have been installed.

Hope it helps:guitar:

---

### Post by nothingspecial on 2009-05-05
Hi. 

I see you have installed openssh-server and openssh-client already. Make sure they are on both machines.

Right click on the network manager icon and click properties. This will tell you the ip address of that machine. 

On your other machine, in your menu, click places then connect to server. In the top box it asks you for a connection method. Change it to ssh.

In the box where it asks what you want to connect to type something like ```
szaemon@192.168.1.2
```. Change szaemon for the other pc`s username and 192.168.1.2 for the ip address of the other machine.

Type your other machines password in the password box.

Check the add bookmark button and choose a name for your other computer.

Click connect and when it asks, tell it to remember the password.

Repeat this process on the other machine.

You should now have an entry in your places menu for the other computer that if clicked will give you full access to that box.

I`m doing this from memory as I`m not on Ubuntu (or gnome) at the moment. Anything that doesn`t work or you don`t understand just post back.

---

### Post by netwarriorwy on 2009-05-05
If you wanna share files it shouldnt be a problem just configure samba.

Lets see. If you've never touched ur router its almost sure you have DHCP activated and you get ip addresses automatically. If you are not receiving your ip addresses from DHCP the you have static address and you can provide your devices with one using the network manager applet on the right top part from your screen. Just right click and click on Edit Connections...

Then choose whether is a wired or wireless connection. You have to enter an ip address, a gateway address (normally 192.168.1.1 or 192.168.0.1), the subnet mask (usually 255.255.255.0) and the dns servers.

You can play with your router writing 192.168.1.1 or 192.168.0.1 in a new tab from your browser. Be careful handling your router, dont change things just for changing.

If you want to access to some other machine just to use a virtual server or a service you can to this:

> ip_address: port[/application]
e.g.: 192.168.1.3:8080/web


:popcorn:

---

### Post by vahnx on 2009-05-05
> **szaemon said:**
> 
What I am trying to do is give each of my computers and only "my" computers complete and total access to each other through my router... or as close to that as possible. Is that a difficult task?


Judging by your posts so far, you have all computers on the same network. I assume by what you mean, giving computers access to eachother, you mean filesharing. Since you already have Samba installed in Linux, go to System -> Shared Folders. There you can add folders to share, or just right click and Share. In Windows you can also right click and under Propterties click share. Then you can access the other computers shares through My Network Places/Network/Homegroup in Windows, and in Ubuntu under Places -> Network. 

If you have any software firewalls you might want to disable them during troubleshooting since you are behind a router anyways. In Ubuntu you can also open Nautilus (Computer) and in the address bar type smb://(IP of other machine)/ShareName to access the share, in Windows in Explorer (My Computer) type in the address bar \\(IP of machine)\ShareName. *sharename is optional, but going to a direct share is faster than scanning for all shares on that computer).

---

### Post by szaemon on 2009-05-05
Thanks you guys or gals for all the help. It always amazes me how people just pick up and start offering help where someone else left off. This is a really good community to be a part of. I hope I get to the point where I can start giving people help.

Thanks again. I'll be back if I still can't figure it out.

---

### Post by szaemon on 2009-05-06
Thanks to all of you for all the help you offered. Nothigspecial, that did the trick. Between remote desktop and openssh, I now have all the access I could want.

vahnx and netwarriorwy, thanks. I'm gonna keep trying to configure Samba just for the educational experience, but... WoW! It seems complex.

---

### Post by netwarriorwy on 2009-05-06
That is what makes our community so great...you can be anywhere but there's always someone who can help us...keep up the good work :guitar:

---

