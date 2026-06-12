---
title: "Hi. Some little help needed"
date: 2009-04-28
forum: General Help
---

### Post by Rany . on 2009-04-28
Hello. I am new to linux. I've Installed Ubuntu for a week or so.
I got everything done ok, installation, downloading resources, play games, 
converting DVD, some customization, all thanks to this very useful forum. Cheers! :P:P

Just a couple of things tho ..
1. that when I press Alt+F2, the run command, I don't know how to clear them
 (those I no longer use).
Its nothing big, but I use it quite often. I couldn't find the solution anywhere, 
not here, not in the pocket guide. 
So I appreciate if anyone would point me to the right direction.
2. I accidentally created a folder that has a newline tag /n, which i don't know how to delete.
[COLOR=Blue]drwxr-xr-x   2 root root  4096 2009-04-26 23:30 Ranys?sudo mkdir Ranys[/COLOR]
the folder appeared as
[IMG]http://img123.imageshack.us/img123/8206/oddfolder.png[/IMG]
I don't remember how I did it. Anyway, how can I delete it?

Ps. Is there any AND, OR, NOT option for forum search that I failed to notice?
Thanks!

---

### Post by ade234uk on 2009-04-28
Sorry I did a reply to your question, but did not read it and gave you totally the wrong answer. I have removed this, hopefully someone else can answer for you.

---

### Post by Rany . on 2009-04-29
Anyone?

---

### Post by muteXe on 2009-04-29
```

sudo rm -r <name of your folder here>

```

maybe?

---

### Post by freonchill on 2009-04-29
sudo rm directoryname
it might complain that its not empty

so either
sudo rmdir -rf directoryname
or
sudo rm -rf directoryname

-r recursive
-f force

---

### Post by cariboo on 2009-04-29
See as you are used to using Alt-F2. Press ALt-F2 and type:

```
gksu nautilus
```

This will open Nautilus as root and allow you to remove the directory.

---

### Post by Rany . on 2009-05-05
> **cariboo907 said:**
> See as you are used to using Alt-F2. Press ALt-F2 and type:

```
gksu nautilus
```This will open Nautilus as root and allow you to remove the directory.
Thanks! Finally deleted.


So anyone knows how to clear the Alt+F2 history?

---

### Post by Rany . on 2009-05-16
I tried to get Wifi working following this link:
[http://ubuntuforums.org/showthread.php?t=510352&page=11](http://ubuntuforums.org/showthread.php?t=510352&page=11)
at ***ndiswrapper -ma***, I had to add *SUDO*****in front
At ***loadndisdriver1.9***
it says **bash: loadndisdriver1.9: command not found**
 
How do I detect Windows wireless networks? Never thought I would need wireless until the embarrassment I got today.
I can receive several signals around me when I was on Vista. Where exactly should I click?

I've installed Windows Wireless Drivers
[IMG]http://img42.imageshack.us/img42/8090/wwn.png[/IMG]

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

What do lines the above mean?

Thanks.****

---

### Post by rudy.b on 2009-05-16
> **Rany . said:**
> How do I detect Windows wireless networks? Never thought I would need wireless until the embarrassment I got today.
I can receive several signals around me when I was on Vista. Where exactly should I click?

Click the Network Manager applet in the notification area to select from the available networks in your area.  If you select a secure network, it will prompt you for the authentication credenitials required for the network.

---

### Post by Rany . on 2009-05-16
Thank you Rudy for your reply.
So I click creating new wireless network?
[IMG]http://img41.imageshack.us/img41/3231/63940569.png[/IMG]
[IMG]http://img38.imageshack.us/img38/2570/75057502.png[/IMG]

In Vista it scans for wireless networks and display them graphically, where do I get this in Ubuntu?

Thanks.

---

### Post by Scotty Bones on 2009-05-17
Any detected wireless network should show up right under the Wireless network heading

---

### Post by Rany . on 2009-05-17
Thanks Scotty Bones.
That means I did something wrong. Because there should be at least 2 wifi network here.

Can someone show me how to make it right?

Thanks again.

---

### Post by rudy.b on 2009-05-17
Rany,

You may want to check for your networks using the terminal command:

```
$ iwlist wlan0 scan
```

to verify that your interface is in fact detecting the networks but the Network Manager applet isn't displaying them for some reason (e.g. the SSID is hidden).

---

### Post by Scotty Bones on 2009-05-17
Just a thought. Are you sure you have your wireless drivers installed properly? Judging from your screen shots you might not. I noticed you used the manual method w/ ndiswrapper. Have you tried installing from the restricted drivers manager? System> Administration> Hardware Drivers?

---

### Post by Rany . on 2009-05-17
[B]iwlist wlan0 scan
bash: $: command not found[/B]

[IMG]http://img265.imageshack.us/img265/780/33088038.png[/IMG]

I guess I have not been on the right track?

---

### Post by rudy.b on 2009-05-17
Sorry, try:

```
sudo iwlist wlan0 scan
```

If that doesn't work, you'll need to install the wireless-tools package (although I think you should already have it installed since you were using iwconfig earlier):

```
sudo apt-get install wireless-tools
```

---

### Post by randiroo76073 on 2009-05-17
If all else fails you can try "wicd"

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by Rany . on 2009-05-17
Eh, wireless worked after a crash with compiz.. back to the default 2 desktop...
Strange...

Rebooted, compiz ok, and wireless ok too. I dunno why but its working.

Thanks to all who had responded.

---

### Post by Scotty Bones on 2009-05-17
> **Rany . said:**
> [B]iwlist wlan0 scan
bash: $: command not found[/B]

[IMG]http://img265.imageshack.us/img265/780/33088038.png[/IMG]

I guess I have not been on the right track?

Thats it. When you click on the device, it should show an "Activate" button. That should install the drivers for you and ask for a reboot. After that you should be good to go.


EDIT: Judging by that picture, it looks like you might be running gutsy or hardy? You might want to upgrade to jaunty (9.04)

 Glad to hear all is working for you.

---

### Post by Rany . on 2009-05-18
I am using Xine and Mplayer, how do I get to hear the audio for 3gp from my handphone?
The video is fine but no sound coming ut, it says no codec.

Thanks.

---

### Post by Rany . on 2009-05-21
I can now play 3gp with sound thanks to this thread.
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
I had been lazy, became reliant of others help.

Ok, I can play now,
But with avidemux and deVeDe, the conversion of the audio cannot be performed, no sound in the converted videos.
Any ideas on how I can convert 3gp into mpg, with audio? Anyone with the experience of doing so?
Thanks.

---

### Post by Rany . on 2009-06-04
I was meddling with pcmanfm. 
[http://ubuntuforums.org/showthread.php?t=692238](http://ubuntuforums.org/showthread.php?t=692238)
Everything seemed ok, I removed nautilus.
But then issues arise:
1. Startup time became longer, I hear the startup music, but screen is still black.

2. If I close the first pcmanfm window, which pops up at startup, I cannot open files with a new pcmanfm (txt, htm, jpg). I have to open the app, then drag the file into it.
If I lave the first window on, and double click on files I need opened, I still need to wait 2~3 seconds for the application to launch.

3. I tried to put nautilus back, the one poping up is still pcmanfm, but in process viewer, it is named nautilus.

I must have messed up something, I had wasted whole day doing this. I was hoping my system would go faster, but it turned out the other way round. Can someone help my to solve this?

Thanks.

---

### Post by Rany . on 2009-06-05
Oho, I solved it.



By clean install. :lol:

---

### Post by Rany . on 2009-08-01
Does anyone know how to overcome this?

Only one app can play sounds at one time.
If the webpage I'm visiting has sound, opening exaile won't play.
If exaile already playing, webpage won't have sound. > _<

Thanks.

---

