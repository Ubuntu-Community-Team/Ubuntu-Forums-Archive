---
title: "Dedicated Home Server/pc (TranquilPC) - Advice needed"
date: 2009-01-14
forum: General Help
---

### Post by socistep on 2009-01-14
Hi All,

I'm thinking of buying one of these

[http://www.tranquilpc-shop.co.uk/acatalog/T7-330_Barebones.html](http://www.tranquilpc-shop.co.uk/acatalog/T7-330_Barebones.html)

Primarily to stream music to my squeezeboxes but also as a file backup/transfer and also other services. I also would like to use this as another pc linked up to TV however in the main I am looking to run it low power and headless.

I want to run Ubuntu on this, however I have a few questions that I would appreciate help from the community with.

- What would be best for this install, Ubuntu desktop or server ? I have desktop experience but none for server edition.
- Could I install from a USB stick or would I have to look to get an external CD drive to install ?
- What would be the best way to keep this as low power as possible (it will be on 24hours) - I was looking at auto suspend & wake on LAN as two options
- As mentioned I don't have much server experience, is the only way to interact with the server via a terminal or is there a GUI interface?
- On that theme, if I went with Desktop would remotedesktop/VNC be the best way to log in remotely to the box ?

Any other tips/advice would be recommended, I'm wanting to get this right so all help appreciated...

Ian

---

### Post by Titan8990 on 2009-01-14
1) Servers don't come with a GUI. If you feel comfortable with the CLI then use the server version. This will mean you will not have to purchase/use a monitor, mouse, or keyboard for the server (headless).

2) This can be done but I have not tried it. I can't comment any more on this

3) I let all my desktops and servers run 24/7 with no regards to energy consumption, therefore I can't really comment on this either

4) You can use ssh to remotely manage the server. If you want a GUI there is also webmin and phpmydadmin if you run a AMP server.

5) You still should use ssh and webmin.


What do you plan to do with this server?

---

### Post by socistep on 2009-01-14
Hi Titan

Thanks for the reply, I'm mainly looking at using it for streaming music to my Squeezebox players but also as a central file store/share & backup between various laptops etc.

I was looking at a NAS to do the above but made the decision to go for a low power PC for the same price as I feel it gives more value for money

Ian


> **Titan8990 said:**
> 1) Servers don't come with a GUI. If you feel comfortable with the CLI then use the server version. This will mean you will not have to purchase/use a monitor, mouse, or keyboard for the server (headless).

2) This can be done but I have not tried it. I can't comment any more on this

3) I let all my desktops and servers run 24/7 with no regards to energy consumption, therefore I can't really comment on this either

4) You can use ssh to remotely manage the server. If you want a GUI there is also webmin and phpmydadmin if you run a AMP server.

5) You still should use ssh and webmin.


What do you plan to do with this server?

---

### Post by Titan8990 on 2009-01-14
I have never attempted a streaming media server but a backup server should be fairly simple.

You can use a rsync server on the Ubuntu server and Delta copy if the clients use Windows or plain rsync for other linux clients.

---

### Post by socistep on 2009-01-14
> **Titan8990 said:**
> I have never attempted a streaming media server but a backup server should be fairly simple.

You can use a rsync server on the Ubuntu server and Delta copy if the clients use Windows or plain rsync for other linux clients.

Its really easy...the Squeezebox interacts with a server program called Squeezecenter, this would just run on the box and the music players would have 24hr access to it, I have it running on my laptop but its a pain having to switch on/off

---

### Post by stefangr1 on 2009-01-14
What you could also do is build a system like:
- IO-board with energy efficient chipset (like AM780G)
- energy efficient amd X2 (like) 4450e
- 2 GB ram
- sata harddisk of 500GB (there are also some low energy drives like the samsung ecogreen, which uses only 3W
- consider an energy efficient psu (corsair has some that just came out)

When you keep everything as simple as possible, this would cost you only a fraction more then the Tranquil box, at an idle power consumption of ~40W (5 pounds a month?). Also, the Tranquil box has only a 3GB harddrive.

Why? Because a setup like this has much more power, and you can configure it as you like. You could for example add an extra network card, so that you can use your server as a router / firewall / dhcp server / pxe server. Another idea is to put only a base system on it, and then put the things that are more sensitive to configuration on virtual machines that you can access from the web (vmware server 2). In this way, when something goes wrong essential applications like your fileserver will still continue to operate.

To install the os, you can just take the harddrive out, put it in another pc temporarily and install it from there (if you don't have an external disk drive or a pxe server).

---

### Post by socistep on 2009-01-15
Hi Stefan,

Thanks for the post, I did look into building something but it was mainly the time element that contributed against it ....I'm not ruling it out for definate but would all be very new to me.

In terms of installing the OS - I hadn't thought of that approach, looks like something that would be feasible for me.

Thanks
Ian

__> **stefangr1 said:**
> What you could also do is build a system like:
- IO-board with energy efficient chipset (like AM780G)
- energy efficient amd X2 (like) 4450e
- 2 GB ram
- sata harddisk of 500GB (there are also some low energy drives like the samsung ecogreen, which uses only 3W
- consider an energy efficient psu (corsair has some that just came out)

When you keep everything as simple as possible, this would cost you only a fraction more then the Tranquil box, at an idle power consumption of ~40W (5 pounds a month?). Also, the Tranquil box has only a 3GB harddrive.

Why? Because a setup like this has much more power, and you can configure it as you like. You could for example add an extra network card, so that you can use your server as a router / firewall / dhcp server / pxe server. Another idea is to put only a base system on it, and then put the things that are more sensitive to configuration on virtual machines that you can access from the web (vmware server 2). In this way, when something goes wrong essential applications like your fileserver will still continue to operate.

To install the os, you can just take the harddrive out, put it in another pc temporarily and install it from there (if you don't have an external disk drive or a pxe server).

---

### Post by mixmaster on 2009-01-15
I'm actually in the process of installing a music server based on squeezebox/squeezecenter on just one of these boxes.

So, yes you can install from a USB stick.  If you have another ubuntu intrepid box it will build you a live install USB directly from the system/administration menu, or you can clone an existing setup using remastersys.

Servers have no GUI, but squeezecenter is configured and administered via a web browser so once you have it running you can simply point firefox at [http://servername:9000](http://servername:9000) and do what you want from there.  

The power consumption is so low that I would not bother with wake-on-lan.  TBH, I don't know how well the squeezebox devices would cope with a server which wasn't there all the time.  It should work but I haven't tried it.

If you are not comfortable with command line administration, I would go with a normal desktop install.  The dual-core atom is more than adequate for this as well as music & file sharing.  How you access it is dependent on what other machine(s) you have.  I actually hooked up a screen and keyboard for installation and since then I've used ssh from other linux boxes.  If you start your ssh session with a -x parameter then you can cause any graphics apps you want to run on the T7 to appear on your local desktop.  If you really want the whole T7 desktop to appear on another machine you could look at FreeNX but I suspect this is overkill.

This is a nice, quiet, compact machine.  However, one word of warning.  I ordered a configured option (ie with memory and disk already installed) and they have a nasty habit of glueing things to each other - like the sata and power cables to the drive!  Mine is going back for rework because they delivered it with the wrong size HD and I don't feel like attacking it with a heat gun to melt the glue.  They will happily omit the adhesive but you have to know to ask.  I suspect it is done that was because their main customer base is for Windows-Home-Server devices.

Someone else suggested build-from-scratch.  You can do this but you will be hard pressed to achieve anything as neat.  If it is going to be hidden away somewhere that doesn't matter but mine is likely to end up in with the hifi so appearance was significant.

---

### Post by socistep on 2009-01-16
Hi Mixmaster,

Thanks for replying, think you will be a good contact to have !

Have added some comments/further questions below



> **mixmaster said:**
> I'm actually in the process of installing a music server based on squeezebox/squeezecenter on just one of these boxes.

So, yes you can install from a USB stick.  If you have another ubuntu intrepid box it will build you a live install USB directly from the system/administration menu, or you can clone an existing setup using remastersys.

**Have seen this and it looks pretty easy to set-up **

Servers have no GUI, but squeezecenter is configured and administered via a web browser so once you have it running you can simply point firefox at [http://servername:9000](http://servername:9000) and do what you want from there. 

**Agreed, should be pretty easy to interact with SC if I was to go for the server install**

The power consumption is so low that I would not bother with wake-on-lan.  TBH, I don't know how well the squeezebox devices would cope with a server which wasn't there all the time.  It should work but I haven't tried it.

**Do you invoke any power saving or just keep it running 24/7 ?**

If you are not comfortable with command line administration, I would go with a normal desktop install.  The dual-core atom is more than adequate for this as well as music & file sharing.

**I am relatively comfortable with CLI and think I would be able to do interact with the server edition, however I am more then likely going to go for the Desktop edition**

  How you access it is dependent on what other machine(s) you have.  I actually hooked up a screen and keyboard for installation and since then I've used ssh from other linux boxes.

**I will probably access from another Linux machine, for installation it will be similar I'll temporarily hook up a monitor/keyboard**

  If you start your ssh session with a -x parameter then you can cause any graphics apps you want to run on the T7 to appear on your local desktop.  If you really want the whole T7 desktop to appear on another machine you could look at FreeNX but I suspect this is overkill.

**So you log into the T7 via SSH on a terminal and then when running a program it will open as normal onto the other box ? Quite interested in this, do you have any further links I can look at ?**

This is a nice, quiet, compact machine.  However, one word of warning.  I ordered a configured option (ie with memory and disk already installed) and they have a nasty habit of glueing things to each other - like the sata and power cables to the drive!  Mine is going back for rework because they delivered it with the wrong size HD and I don't feel like attacking it with a heat gun to melt the glue.  They will happily omit the adhesive but you have to know to ask.  I suspect it is done that was because their main customer base is for Windows-Home-Server devices.

**I was looking at the barebones option and adding my own HDD as I want to add a 1tb drive which they don't do as an option, good point though, will be one thing to check with them**

Someone else suggested build-from-scratch.  You can do this but you will be hard pressed to achieve anything as neat.  If it is going to be hidden away somewhere that doesn't matter but mine is likely to end up in with the hifi so appearance was significant.

[B]I don't have the time really for it plus it will more then likely be on view so similar consideration to you

What other applications have you running on the box ? Is it easy to share files with other boxes ?[/B]



Thanks
Ian

---

### Post by BlakeM on 2009-01-16
Very useful/interesting thread. I'm also eager to know how this -x parameter works. I'll look into it myself. I have a few questions related to this thread:

[LIST=1]
[*]So no one thinks Wake on LAN is worth having to save electricity?
[*]Are Squeezebox and Squeeze Centre the best option for streaming a music library over a network? I was looking at VLC but it doesn't seem to list the contents of the library like iTunes or Winamp?
[/LIST]

---

### Post by socistep on 2009-01-16
> **BlakeM said:**
> Very useful/interesting thread. I'm also eager to know how this -x parameter works. I'll look into it myself. I have a few questions related to this thread:

[LIST=1]
[*]So no one thinks Wake on LAN is worth having to save electricity?
[*]Are Squeezebox and Squeeze Centre the best option for streaming a music library over a network? I was looking at VLC but it doesn't seem to list the contents of the library like iTunes or Winamp?
[/LIST]

Its definately the best option for me, this is the main reason I'm getting a T7 - Have you done much research into the Squeezebox kit ? I have a Boom & a Duet and are very happy with both of them

[www.slimdevices.com](www.slimdevices.com)

Are you wanting to play the music on your pc or through a Network music player ? With squeezecenter you can stream through a player on your pc as well as the Duet/Boom etc.

In terms of WOL, I'm open to trying it to be honest, it seems to be popular on the Squeezebox forums for power saving

---

### Post by jv13613 on 2009-01-16
try unetbootin to do a usb install.

for the os you could install ubuntu server and then install ubuntu-desktop.

---

### Post by mssever on 2009-01-16
Ian,

As far as SSH goes, you can just create an alias: ```
alias ssh='command ssh -X'
```and put that on one of your startup files (such as ~/.bashrc). Then you'll always have X forwarding. With that option, windows that you open on the remote machine open on your local machine. Sounds, however, don't get forwarded.

---

### Post by socistep on 2009-01-19
Hi Mssever,

Thanks for the advice, looking forward to trying this out...

> **mssever said:**
> Ian,

As far as SSH goes, you can just create an alias: ```
alias ssh='command ssh -X'
```and put that on one of your startup files (such as ~/.bashrc). Then you'll always have X forwarding. With that option, windows that you open on the remote machine open on your local machine. Sounds, however, don't get forwarded.

---

### Post by ac7ss on 2009-01-19
I have streaming audio set up on my Ubuntu box using a full LAMP setup running Ampache. It works wonderfully to listen to my collection from home.
I am looking for a way to stream video files to VLC.

---

### Post by mssever on 2009-01-19
> **ac7ss said:**
> I have streaming audio set up on my Ubuntu box using a full LAMP setup running Ampache. It works wonderfully to listen to my collection from home.
I am looking for a way to stream video files to VLC.
Please don't hijack threads to ask off-topic questions. Better to start your own thread.

---

### Post by ac7ss on 2009-01-27
I thought this was about media serving. Is not streaming to VLC media serving?

---

### Post by mixmaster on 2009-01-27
socistep, sorry for the delay in getting back to this thread.

> **mssever said:**
> Ian,

As far as SSH goes, you can just create an alias: ```
alias ssh='command ssh -X'
```and put that on one of your startup files (such as ~/.bashrc). Then you'll always have X forwarding. With that option, windows that you open on the remote machine open on your local machine. Sounds, however, don't get forwarded.

This will work but it is better to use the ssh configuration files.

Create a file .ssh/config in your home directory.  You can use this to do all sorts of clever things.  This is an example from my office system:
```

Host def1 banana dogfite ga2004 ldcluster-70 ldcluster-28 dvt000003 dvt100003 ga2004216 predvt101038 war famine plague death ronnie destiny1 destiny2 dvt100050 dvt000140 hogfather destiny3 destiny4
        User root
        Port 26
        IdentityFile /home/mixmaster/.ssh/id_lodestone
        StrictHostKeyChecking no

Host grail south compass west
        ForwardX11 yes
        User mixmaster
        IdentityFile /home/mixmaster/.ssh/id_gsa

```
The Host line identifies the system(s) to which the options work.
The rest are the X11 options which apply to that system.
In this case the first batch are test systems without graphics.  I always log in as user root using a backdoor port (26).  Validation is via the  key file id_lodestone (generated by ssh-keygen).
The second batch are shared systems with graphics.  ForwardX11 has the same effect as the -X option and I use a different key.

Basically, the result of these is that I can log onto any of the named systems without password authentication and with the correct userid and options set up.  Setting up ssh like this is a bit of a chore but is well worthwhile if you frequently jump between machines.

The various config options can be found here [http://tldp.org/LDP/solrhe/Securing-Optimizing-Linux-RH-Edition-v1.3/chap15sec121.html](http://tldp.org/LDP/solrhe/Securing-Optimizing-Linux-RH-Edition-v1.3/chap15sec121.html)

You also asked:
*Do you invoke any power saving or just keep it running 24/7 *?
Currently I don't bother with power saving.  I've had so many obscure problems with this on a variety of machines that I'd rather avoid it if possible.  I may revisit this later.

*What other applications have you running on the box ? Is it easy to share files with other boxes ?*
File sharing is easy - I simply use scp which works like a cp command but between boxes.  If you have the ~/.ssh/config set up correctly it doesn't even do any identity checking.  If you are more adventurous you can set up NFS (or samba if you have windoze boxes in the mix).  Or try sshfs which does much the same thing but entirely from user space without any server side setup.
As for other apps, currently I'm still setting things up.  I'll probably put apache and possibly a mailserver on it eventually.

CAVEAT:
If you set up two machines with trusted ssh access via the method set out above then if one is compromised the other is also vulnerable, so be sure of your boundary security.

---

### Post by mssever on 2009-01-27
> **ac7ss said:**
> I thought this was about media serving. Is not streaming to VLC media serving?It's about a series of questions the OP asked that are inspired by but unrelated to Squeezebox and have nothing at all to do with VLC. Read the thread. If it were about media serving, I probably wouldn't have posted in the thread since I have no experience in that subject.

The proper way to ask a question of your own is to start your own thread. When you post your own question in an existing thread, you add noise to the original topic and the people following the existing thread may very well not be able to help, anyway (especially if it's unrelated as in this case).

> **mixmaster said:**
> This will work but it is better to use the ssh configuration files.

Create a file .ssh/config in your home directory.  You can use this to do all sorts of clever things.  This is an example from my office system:
```

Host def1 banana dogfite ga2004 ldcluster-70 ldcluster-28 dvt000003 dvt100003 ga2004216 predvt101038 war famine plague death ronnie destiny1 destiny2 dvt100050 dvt000140 hogfather destiny3 destiny4
        User root
        Port 26
        IdentityFile /home/mixmaster/.ssh/id_lodestone
        StrictHostKeyChecking no

Host grail south compass west
        ForwardX11 yes
        User mixmaster
        IdentityFile /home/mixmaster/.ssh/id_gsa

```
That's good to know. I don't recall reading about that in the ssh man page; but then again, it's probably been many years since I've read ssh client documentation, and the last time I read it, I very well might not have had a use for a ~/.ssh/config.

---

### Post by cjssmo on 2009-03-05
Check out Ampache, it's a great music streaming server.

Ampache.org

---

### Post by mortuk on 2009-03-15
I am awaiting delivery of a Tranquil BBS2 Advanced and was also considering making myself some kind of Ubuntu Home server (similar to Windows Home Server)

Really liking the Drive Extender and storage pool features on WHS. Will you be recreating these in Ubuntu?

---

### Post by lummie on 2009-04-14
I bought a BBS2 a few weeks ago and had fun trying to install hardy server from a bootable usb stick (failed when it tried to detect the cdrom media funny enough), eventually borrowed a usb cd-drive and ubuntu server installed with no problems.  

I actually installed it to an 8Gb Corsair Voyager GT USB flash drive which is the OS drive, so I have the full 5 bays available for raid and can re-install the OS without messing with partitions etc and risk loosing any data.

I'm using mdadm for the raid, running svn server / samba / cups / apache. At some point I'm going to stick MediaTomb on it.

Hardy installs (incorrectly) with the realtek 8169 ethernet driver which I had a nightmare with when copying large files to the box. Build and use the r8168 instead.

I've blogged setting up the raid and bits at [http://lummie.co.uk](http://lummie.co.uk)

Matt

---

