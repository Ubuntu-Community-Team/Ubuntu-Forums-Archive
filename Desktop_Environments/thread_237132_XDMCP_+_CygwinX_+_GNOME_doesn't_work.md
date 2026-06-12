---
title: "XDMCP + Cygwin/X + GNOME doesn't work"
date: 2006-08-15
forum: Desktop Environments
---

### Post by miketech on 2006-08-15
Hi,

I wanna use Cygwin/X (on Windows) to login into my GNOME desktop (Ubuntu Dapper) via XDMCP. 

With Cygwin/X (Windows) + Gentoo it worked. Now I have installed Ubuntu and it doesn't any longer. The strange thing is:

It doesn't work with GDM, KDM, XDM, when I wanna login into GNOME. But when I login into fluxbox, or XFCE it is working. And if I don't use Cygwin/X with Windows, but another Linux machine it is working with GNOME.

When I try to login into GNOME the cygwin/X on the windows machine crashes and I get a gdm_slave_xioerror on the linux machine.

Do you have any idea, why fluxbox and XFCE is working, but GNOME isn't when I try to connect from a windows machine? I see the GDM, but when I try to login it hangs up, or crashes.

Greetings

Mike

---

### Post by benklaasen on 2006-08-22
Hi Mike - 

I'm having exactly the same problem. XDMCP is enabled on both of my Dapper boxes, and I can get an XDMCP login from either to the other, but Cygwin on my third box fails to open a login screen. I've got both KDE and Gnome installed on the ubuntu boxes and I'm using GDM as my display manager in both cases.

What's the command you're using to start an XDMCP session from the Windows box?

I'm using xwin -query ububox :0

Show me the complete output that you get when launching xwin.

cheers
Ben

---

### Post by miketech on 2006-08-22
Hi,

well I get the login screen.

With the command:

Xwin -query 192.168.0.15


I also can login with fluxbox, xfce. Only Gnome isn't working. Then Cygwin crashes (all Cygwin windows are closed suddenly), or it hangs up. So it is not possible to get a log, because in the one case the window is closed suddenly, and in the other case I can't use it any more, because everything hanged up.

But from other linux boxes I can login to my Gnome Desktop. Only Cygwin + Gnome isn't working.



First I had problems with getting the login screen. I had to put the hostname and IP of the windows machine into /etc/hosts of the linux box. Maybe this is helpful for you.

---

### Post by ktuulos on 2006-09-10
Hello

I'm a newbie to (K)Ubuntu, but I've been using Debian for quite long, so I was quite surprised to notice that XDMCP + Cygwin/X + KDE froze quite soon. Exactly the same XDMCP + Cygwin/X worked fine with Debian 3.1 :-(

Does anyone know about any workarounds for this? Now it seems that I just need to switch back to Debian :-(

   - Kalle

---

### Post by alanhs on 2006-09-19
Hi folks, I am seeing a similar (if not exactly the same) problem. I get the Gnome Desktop manager login, when I login, the whole session just dies. Nothing very interesting in the log files.

Rather curiously, in the middle of composing this, I installed some updates on the Ubuntu machine and now the cygwin window on my M$ machine is outputting this:-

      6 [main] xwin 2972 _cygtls::handle_exceptions: Error while dumping state (
probably corrupted stack)
Segmentation fault (core dumped)

Where as before it was saying this:-

      7 [sig] xwin 3192 C:\cygwin\usr\X11R6\bin\xwin.exe: *** fatal error - C:\c
ygwin\usr\X11R6\bin\xwin.exe: *** called with threadlist_ix -1
Hangup.

Alan

---

### Post by miketech on 2006-09-19
Hi Alan,

this is exactly what I get too. I've already installed the newest version of cygwin. When I use the newest version of cygwin, start fluxbox and start gnome-session simply nothing happens. And if I start gnome with the newest cygwin nothing happens too, or it crashes.

Still don't have a solution for this.

Greetings

Mike

---

### Post by amohanty on 2006-10-01
Edit: So I  mapped the IP to the hostname in %WINDIR%/system32/drivers/etc/hosts, and lo and behold login screen!!!

HTH the next person to run into this.

AM

And the worst part of it is that cygwin+xdmcp+gnome worked really nicely with ubu 5.10.

Fortunately it doesnt crash all over the place for me, my problem is I dont get the damn login screen. All I get is the Cygwin/X window with the checkered/gray background.

A **tcpdump** on the dapper host tells me that its getting upd pkts over 177 but no X in the process list.

Something went horribly wrong :( The question I have is how do we go about fixing this?

AM

PS some more details
cmd:  E:\>e:\bin\run.exe e:\usr\X11R6\bin\XWin.exe :1 -query 192.168.0.2 -broadcast

XWin.log contents:
> _XSERVTransmkdir: Owner of /tmp/.X11-unix should be set to root
(II) XF86Config is not supported
(II) See [http://x.cygwin.com/docs/faq/cygwin-x-faq.html](http://x.cygwin.com/docs/faq/cygwin-x-faq.html) for more information
winCreateBoundingWindowWindowed - Setting normal windowstyle
MIT-SHM extension disabled due to lack of kernel support
XFree86-Bigfont extension local-client optimization disabled due to lack of shared memory support in the kernel
(--) Setting autorepeat to delay=500, rate=31
(--) winConfigKeyboard - Layout: "00000409" (00000409) 
(--) Using preset keyboard for "English (USA)" (409), type "4"
(--) 3 mouse buttons found
Could not init font path element /usr/X11R6/lib/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/CID/, removing from list!
XDM: too many retransmissions, declaring session dead
FreeFontPath: FPE "/usr/X11R6/lib/X11/fonts/misc/" refcount is 2, should be 1; fixing.
(II) XF86Config is not supported
(II) See [http://x.cygwin.com/docs/faq/cygwin-x-faq.html](http://x.cygwin.com/docs/faq/cygwin-x-faq.html) for more information
winCreateBoundingWindowWindowed - Setting normal windowstyle
MIT-SHM extension disabled due to lack of kernel support
XFree86-Bigfont extension local-client optimization disabled due to lack of shared memory support in the kernel
(--) Setting autorepeat to delay=500, rate=31
(--) winConfigKeyboard - Layout: "00000409" (00000409) 
(--) Using preset keyboard for "English (USA)" (409), type "4"
(--) 3 mouse buttons found
Could not init font path element /usr/X11R6/lib/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/CID/, removing from list!


---

### Post by mlebek on 2006-10-18
Hi, 

i have the same problem with gentoo, kde, cygwin & Win XP. 

I think it has something to do with the combination of xp, cygwin and the chipset of the client. 

i have 4 clients with Via KM266 chipset. Win98 & cygwin works fine, but under Win XP cygwin freezes after some minutes. open and close openoffice after login accelerate the process.

what chipsets do your clients have?

---

### Post by Toasterboy on 2006-10-31
Looks like several ports on the XP firewall need to be open.  The non-obvious one is 16001, which is i think remote sound.  
Since the XP firewall does not ack packets it drops, we crap out when sound tries to play and bad things(tm) happen when the requests time out.  Someone probably ought to change the logon sound code to fail more gracefully if packets on 16001 are going down a rabbit hole.

Looks like you will need to add ports UDP 177, TCP 6000, and TCP 16001 on the exceptions list for the Windows XP firewall.

---

### Post by miketech on 2006-10-31
But also a completely disabled firewall doesn't help.

Greetings

Mike

---

### Post by ktuulos on 2006-11-15
> **mlebek said:**
> Hi, 
I think it has something to do with the combination of xp, cygwin and the chipset of the client. 


I have the same problem with all my three different computers:
- one being about 1 year old IBM T43 laptop /w WinXP SP2
- one being about 1 year old VIA chipset based desktop PC / WinXP SP2
- one being about 5-6 years old Pentium II desktop computer (Fujitsu ErgoPro)/ Win2k

The T43 has firewall and virus scanner on, other computers don't have any firewalls or virus scanners.

The newer desktop PC is connected with 100MB cable, T43 with cable or WLAN (depending on which part of house I am), the old desktop with WLAN.

Any further ideas, anyone :-)

---

### Post by doniv on 2006-12-16
I've been struggling with the same problem and it looks like XWin is depending on XFS to provide fonts.  On ur ubuntu box, do an 'apt-get install xfs'

Then configure xfs to start with '-daemon -droppriv -port 7100' options

Then make sure xdmcp is enabled in gdm - /etc/gdm/gdm.conf - in the xdmcp section

Then the last thing to do is comment the 'no-listen=tcp' line in the /etc/X11/fs/config file

Restart and check if its working now.  I'm still having problems which I think are being caused due to UDP being firewalled :(

---

### Post by prioret on 2006-12-17
I was having the exact same problem. I fixed it by editing the windows host file to add the Ubuntu machine. Then, I edited the /etc/hosts on ubuntu.. it had a weird entry like:
127.0.1.1 %myhostname%

I changed that line to:
%myhostip% %myhostname%

make your proper substitutions for %myhostip% and %myhostname%

---

### Post by Didjit on 2007-03-20
Anyone get this working with Windows Cygwin? [http://www.theevilpixel.com/?q=node/67](http://www.theevilpixel.com/?q=node/67)

Didjit

---

### Post by rdcwayx on 2007-03-22
> **Didjit said:**
> Anyone get this working with Windows Cygwin? [http://www.theevilpixel.com/?q=node/67](http://www.theevilpixel.com/?q=node/67)

Didjit

Could you please explain more detail about the link? 

I still have the same problem on Cygwin/X+ubuntu.

---

### Post by Didjit on 2007-03-23
This is just to get remote sound working.

What problems are you having?

I found a really nice front end client for XDMCP/Cygwin, [http://www.linuxtsc.org/](http://www.linuxtsc.org/)  Works great for me.

Didjit

---

### Post by markjf on 2007-05-01
did anyone get this working?
i'm getting hangups after logging in from cygwin/X, but xming works perfectly well.

i can stick with xming but seems a shame i can't get cygwin/x working too.

---

### Post by Jhongy on 2007-05-03
Oddly enough, I can't get XMing to log  into Gnome -- KDE or xfce work fine. Gnome just gives a brown screen.

I found a workaround though:

If, before logging in, you selection sessions-> language, and change the language (say, from US english to UK english), then you can log in just fine.

The thing is, you have to change the language each time you log in :confused: 

So -- the million dollar question is... what is causing this and how do I fix it properly?

---

### Post by martink on 2007-05-21
Hi,

I am a newbie to Ubuntu and had the problem that the Cygwin/X Xwin exe hung accessing my dapper host after log in. Nothing helped until I used the screen resolution settings for XWin -screen option ... and as of a sudden all worked as expected.
E.g.: 
> XWin.exe -query 192.168.128.128 -screen 0 1024 768

---

### Post by starfry on 2007-05-25
Hello,
I'm happy to reply I am getting the same problem. If I use Cygwin/x to connect to my Xubuntu box this happens. If I use Hummingbird Exceed, it does not.

Any suggestions to get this working?

Thanks!

---

### Post by starfry on 2007-05-26
Hello, an update: I have found XMing ([http://www.freedesktop.org/wiki/Xming](http://www.freedesktop.org/wiki/Xming)) and this works fine.

---

### Post by pn4577 on 2007-06-05
Hi folks,

I had the same prob with cygwin and Dapper (the kubuntu version).
First thing i had to do is to edit the */etc/kde3/kdm/kdmrc* file. In the *[Xdmcp]* section change 
```
Enable=false
``` to ```
Enable=true
```
By default no remote host has access to the ubuntu host. But there's an other file to edit: */etc/kde3/kdm/Xaccess*. Go to the line ```
#*                                      #any host can get a login window
``` and uncomment it to ```
*                                      #any host can get a login window
``` Be aware that this might be a security risk if everybody can get access to the login screen!
After changing (and saving ;) ) the files, you have to restart kdm: ```
sudo /etc/init.d/kdm restart
```
Now you can log on from the remote machine with something like ```
XWin -query <kubuntu-host>
```
I know, it's just for KDE, but Gnome should have similar configuration settings.

Cheerio

---

### Post by bford16 on 2007-06-24
I was able to make XDMCP/Gnome work with Windows XP and Ubuntu Feisty 7.04, by following these steps.

1. Make sure xdmcp is enabled in gdm - /etc/gdm/gdm.conf - in the xdmcp section.
2. I replaced the built-in Windows Firewall with the [free as in free beer] Zonealarm firewall.  Make sure you disable the Windows Firewall once ZA is installed.

Next, I ran cygwin and attempted to login to my Ubuntu account.  Cygwin connects to the remote computer just fine, but Gnome won't load when I log in. Zonealarm throws up a red alert on the Windows machine.

Here is the tricky part. You have to open the Zonealarm Control Center (just double-click the Z icon in the system tray on Windows).  Find the Firewall log section and look for the connection that was just blocked.  You must add this item to the Trusted zone.

Close all cygwin windows, then restart cygwin and log in to Ubuntu. It should work. But no sound yet. I still have to figure out how to enable that.

---

### Post by arthurdent71 on 2007-08-02
It seems like there are several solutions to several problems here.

1. To make XDMCP work at all 
2. xdmcp/xdm bugs out after you got connected and logged in.

I have the second problem. Gdm start up and let me log in but with an errorbox telling me that configuration deamon did'nt get a response. leaving me with a desktop with no menues at all.

Anyone recognize these sympthoms? 
Any known bugs with gdm and XDMCP? 

I use Xming and gnome and have had this configuration up and running on same machine for days with no fault until this.

I'll get back with log info on this matter.

Kindest regards

edit:
Found loads of tips with second problem @ [https://launchpad.net/ubuntu/+source/control-center/+bug/61381]("https://launchpad.net/ubuntu/+source/control-center/+bug/61381")

---

### Post by DCToblerone on 2007-08-03
It seems that one of the major problem with hanging on login and logout is that gnome is trying to contact an esd server on port 16001. Many places say to open up this port with Windows firewall. You do need to do this but it's not enough. You need a server that is listening on port 16001 that is able to respond. So you need to download and run this esd server:

[http://www.liquid-reality.de/main/projects/esound](http://www.liquid-reality.de/main/projects/esound)

Now, not only does xdmp/gnome no longer hang, you also get a bonus: sounds! (As long as you remember to enable Enable software sound mixing (esd) checkbox under System, Preferences, Sound, Sounds tab)

To get the clipboard working, I also made this change in /etc/gdm/gdm.conf-custom. I'm not sure this is necessary (I think it is) but it doesn't seem to hurt.

[daemon]
KillInitClients=0

I also rebooted the machine (probably to get gdm to restart) and now everthing is working.

P.S. some sites suggest opening port 35091 too, but this didn't seem to do anything for me.

P.P.S. The reason why the zonealarm install worked was probably because zonealaram immediately returned connection refused on port 16001 and gnome went on its way without asking again. But the Windows firewall returns nothing but silence (even with the port open) so gnome waited and waited and waited-- finally timing out and putting up an error.

P.P.P.S. Someone needs to fix gnome or configure it to honor an unchecked Enable Software Sound mixing (ESD) option on login and logout.

Hope this helps.
Dave

---

### Post by Jayasimha on 2007-10-15
Hi,

I am new to ubuntu. I have been using redhat these days. I recently installed ubuntu on my system and I wanted to remotely login to it using cygwin. It is working fine with my fedora system but with ubuntu its not working.

heres the output that i get...

$ xwin -query 10.225.76.155
Welcome to the XWin X Server
Vendor: The Cygwin/X Project
Release: 6.8.2.0-2

Contact: [email]cygwin-xfree@cygwin.com[/email]

XWin was started with the following command line:

xwin -query 10.225.76.155

_XSERVTransmkdir: Owner of /tmp/.X11-unix should be set to root
winValidateArgs - g_iNumScreens: 1 iMaxConsecutiveScreen: 1
(II) XF86Config is not supported
(II) See [http://x.cygwin.com/docs/faq/cygwin-x-faq.html](http://x.cygwin.com/docs/faq/cygwin-x-faq.html) for more information
(==) FontPath set to "/usr/X11R6/lib/X11/fonts/misc/,/usr/X11R6/lib/X11/fonts/TT
F/,/usr/X11R6/lib/X11/fonts/Type1/,/usr/X11R6/lib/X11/fonts/CID/,/usr/X11R6/lib/
X11/fonts/75dpi/,/usr/X11R6/lib/X11/fonts/100dpi/"
winDetectSupportedEngines - Windows NT/2000/XP
winDetectSupportedEngines - DirectDraw installed
winDetectSupportedEngines - DirectDraw4 installed
winDetectSupportedEngines - Returning, supported engines 00000007
winSetEngine - Using Shadow DirectDraw NonLocking
winAdjustVideoModeShadowDDNL - Using Windows display depth of 32 bits per pixel
winFinishScreenInitFB - Masks: 00ff0000 0000ff00 000000ff
MIT-SHM extension disabled due to lack of kernel support
XFree86-Bigfont extension local-client optimization disabled due to lack of shar
ed memory support in the kernel
(--) Setting autorepeat to delay=500, rate=31
(--) winConfigKeyboard - Layout: "00000409" (00000409)
(--) Using preset keyboard for "English (USA)" (409), type "4"
Rules = "xorg" Model = "pc105" Layout = "us" Variant = "(null)" Options = "(null
)"
(--) 3 mouse buttons found
Could not init font path element /usr/X11R6/lib/X11/fonts/CID/, removing from li
st!
winPointerWarpCursor - Discarding first warp: 837 494

after this it doesnt go any further. Is there any solution for this..

---

### Post by ilsd on 2007-10-28
try 
$ xwin -query -ac 10.225.76.155

instead of 
$ xwin -query 10.225.76.155

But XWin and kdm (Xdmcp) do not work properly on my pc: client fall in deadlock and I forced to hard-shutdown session and restart kdm :(

---

