---
title: "Help?  Update broke my Internet"
date: 2006-09-15
forum: Desktop Environments
---

### Post by luckylucky on 2006-09-15
I'm hoping someone can help me out here...

I just did an update (you know how Ubuntu notifies you when updates are available) and after a reboot (required for updates) my Internet no longer works (I'm posting this from another computer).

In the notifications area (near the clock) there is a little networking icon with a red "do not enter" symbol.  Clicking on it I get the following message.

"Please contact your system administrator to resolve the following problem:  SIOCGIFFLAGS error: No such device"

Furthermore, when I go to investigate my network devices I can no longer see eth0 (my standard network card to the internet).  It just magically disappeared.

All this from doing an update less than an hour ago.

Any ideas on what to do here?  I'm completely stumped.  Thanks for your help on this.

---

### Post by xyz on 2006-09-15
> Announcement
There was a problem with a recent update. If you have updated your Ubuntu system on September 14, 2006, and are unable to log into your system, please follow these instructions. We apologize for the inconvenience.

We are aware of the forums speed issues. We have requested more ram from Canonical for our database server and currently we have no ETA.
[http://ubuntuforums.org/showthread.php?t=257459](http://ubuntuforums.org/showthread.php?t=257459)

---

### Post by linuxNewb on 2006-09-15
NO THIS IS A SEPERATE ISSUE!!!

I just updated this morning, and my internet is now broken. I'm having to use a windows machine to access this forum. X-server is fine, it's jusy my internet. Pages don't come up in the browser, and Network Tools -> Ping actually freezes up! What's that about?

How can I roll-back to fix my internet until this is resolved?

---

### Post by luckylucky on 2006-09-15
Thanks for a post to that link but it doesn't apply to what I'm experiencing.  As the guy above me stated, this is a different problem.  Though I'm sorry that he (and possibly others) is experiencing the same issue, I'm interested (not glad) to know that it isn't just me or something wrong on my end.  After spending some time on it I'm glad to at least know that it wasn't something I did (though thinking about it I'm sure I didn't do anything that would precipitate this result).

Me, the other guy, and by the sounds of it soon to be many people appreciate any guru that can come to the rescue here.  Thank you in advance!

---

### Post by dietrying on 2006-09-15
i also have problems with my internet connection since last update, but my pc works with a wireless device ra0. the connection works sometimes, then it stopps working. Sometimes a reboot helps, reconfiguring the network device doesn't change anything. Strange strange update :lol:

---

### Post by linuxNewb on 2006-09-15
More details...

Unlike luckylucky, I can still see my eth1. In fact my wireless indicator shows that I am connected to my wireless router. Everything appears fine, but I cannot access the internet or even my router (to which I'm supposedly connected). When I try to ping a host or ip address from Network Tools -> (Ping tab), It freezes. It does not show any output from the ping command, and the actual window itself freezes prompting the gnome alert to close the application.

---

### Post by linuxNewb on 2006-09-15
After rebooting again, everything is fine -- yes I'm embarrased.

---

### Post by evillawngnome on 2006-09-15
I love linux, and im glad you do too.
But please, call it your internet access, not your internet.
Keep using linux, and keep asking for help when you need it. Dont be ashamed to be new, we were all new once and sometimes the easy stuff slips by us too.

---

### Post by luckylucky on 2006-09-16
Ok, so I've reformated and did a fresh install of Ubuntu 6.06.1  After doing the fresh install it worked fine, but then after doing the update it again broke the Internet *"ACCESS"* of eth0.  Now I am absolutely convinced that there is some update that is responsable for this.

I need my computer for working... so does anyone have any clues on how to fix the problem described in the first post in this thread?

Thank you.

---

### Post by luca25 on 2006-09-16
I have exactly the same problem.
My opinion is that it is bound to the changes made in the sk98lin/sky2 driver which affect all systems using Marvell Yukon ethernet cards.

In order to get a quick fix to this problem we need a way to downgrade to version .46 but unfortunately I don't know where to find the right package.

Is there anyone who can help us?

PS: I'm forwarding the problem to Ben Collins on launchpad.

---

### Post by luckylucky on 2006-09-16
So I figured that if Ubuntu is broken then I'll jump ship to Xubuntu, which I've successfully used before.

So I installed Xubuntu and it worked perfectly.  Then I did an update (manually selected to do update) and boom, again the same problem.

**[SIZE="5"][COLOR="Red"]From the other posts on this thread I know that I'm not the only one here with this issue, so could someone please figure out what is going on, or at least bring this to the attention of the bigshot Ubuntu developers so that they are somehow aware of this new problem?[/COLOR][/SIZE]**  Thank you.

---

### Post by luca25 on 2006-09-16
Luckylucky, I can understand your disappointment (I have the same problem), but shouting is not the right way to get an answer.

I explained you what (likely) caused the problem in my previous post. I already posted on lauchpad the bug report.

Anyway, if you want an interim fix to your problem, just install a fresh new version of ubuntu/xubuntu/kubuntu 6.0.6.1 but DON'T UPGRADE the kernel, until this problem is fixed.

---

### Post by luckylucky on 2006-09-16
Hi Luca25

The big red text wasn't meant as shouting, just to make it stand out in what is now a long thread of text, so that (hopefully) it will be noticed.  The unfortunate thing about text messages is that you can't "hear" the actual tone of voice, and people can easily missinterpret intentions.  No shouting, just trying to make that paragraph visibly stand out from the rest of the thread.

---

### Post by luckylucky on 2006-09-16
BTW I guess that that's what I'll do... what you suggested Luca25.  I'll just do a fresh reinstall but hold off on the updates for a week or so.  Hopefully it'll get resolved by then.

---

### Post by 8086ed on 2006-09-18
I get a similar problem since a recent update (but AFTER Sept 14th).  When I click on the network manager, it says:


```
Please contact your system administrator to resolve the following problem:

SIOCGIFFLAGS error: No such device
```

Figured I should say something...  Maybe it'll get fixed sooner.

---

### Post by fabertawe on 2006-09-18
Can anyone confirm that this has been resolved yet? I've not updated yet as I have have a Marvell/Yukon network card and according to [the launchpad report]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/60271") "it will be fixed in dapper and edgy before the weekend is up".

I'm tempted to update and find out but then I'm connected to the net through a router so I'd be stuffed if it isn't fixed!

Cheers ... Paul

---

### Post by 8086ed on 2006-09-18
I just fired up apt, and there are some massive updates this morning.  I'll let you guys know if they fix anything.

EDIT:  FYI, here's what my machine is updating:

NEW packages:
  linux-image-2.6.15-27-386 linux-restricted-modules-2.6.15-27-386
UPGRADED packages:
  libgnutls12 linux-386 linux-image-386 linux-restricted-modules-386
  linux-restricted-modules-common **linux-source linux-source-2.6.15** nvidia-glx


> **fabertawe said:**
> Can anyone confirm that this has been resolved yet? I've not updated yet as I have have a Marvell/Yukon network card and according to [the launchpad report]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/60271") "it will be fixed in dapper and edgy before the weekend is up".

I'm tempted to update and find out but then I'm connected to the net through a router so I'd be stuffed if it isn't fixed!

Cheers ... Paul

---

### Post by 8086ed on 2006-09-18
[COLOR=Red][B]RESOLVED

[/B][COLOR=Black]It works now!  Thanks to everybody who worked on fixing it! : )[/COLOR][/COLOR]


EDIT: Just do this:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

then reboot!  Yes!

---

### Post by pccampos on 2006-09-18
Can I shout a little, please?

[SIZE="5"][COLOR="Red"]Thats the second time that a update brakes my system (the first one being the xserver problem that was easy to fix). Now my system is still broken and I need to work! Isn't this LTS version supposed to be trustworthy. I really will stick with Ubuntu, this is the best distribution I ever used, but please let me express my disappointment with this issue.[/COLOR][/SIZE]

Now that I'm calm, I wish to know how I could update my system as the internet is down?

---

### Post by luckylucky on 2006-09-19
I am happy to see a couple of posts from people suggesting that this issue is fixed.  I'm leaving on a trip in a couple of hours so I'm going to refrain from testing this myself until I get back in 10 days as I can't afford to have my laptop messed up while I'm gone.

To the other people who have also experienced this problem, if you do the update could you please post here whether it was successful for you or if the problem persists?  I'm sure that others would like to know if it is *confirmed* to be fixed, and I'll be sure to check here later on too.  Sorry I can't offer my confirmation to everyone at this time; it's just because of the timing of my leaving in a few hours for my trip that I don't have the time right now to do this myself.

---

### Post by beanie on 2006-09-19
Hello.
I've tried the apt-get command but it seems that the command need to connect to the internet. But the problem is that my network card is not detected (caused by the latest update). So, how do I perform the apt-get update command when there is no network adapter detected? Please help. I've been stuck with Windows now...

---

### Post by carontis on 2006-09-19
Well I'm used when something like you told happens to me, to uninstall phisically the eth0 from its slot, reboot the pc login and shutdown. After that, I install again the eth0 (phisically) and boot. At this time everything should works and this happens when to many applications and drivers are loaded after an update. It can happens but it should not... Try what I told and see if it works. If not, then try to do again your connection.

---

### Post by shadeone31 on 2006-09-19
hello

i've just installed the dapper drake this morning.
everything worked fine and i configured my laptop good to start working.

then, i see the upgrade manager asking me to update 179 packets.
i accepted the updates. and my atheros card just disapeared. :(

i'm now stuck without any connection, and unable to make any changes using apt-get because i haven't internet connection. i only can access it using wifi, no ethernet cable is possible here.

after reading this thread, i was thinking the problem was fixed, but it looks like it wasn't, or partialy.

someone else having troubles with atheros cards after update ?
i've tested with a pcmcia atheros chipset card, and also with my internet atheros mini pci card... without any succes.

thanks for any help you guys can provide :)

---S

---

### Post by ruimoura on 2006-09-19
Did someone tried to put the DNS servers manually on the internet configuration?

Because that&#347; what happend to me. Everytime i reboot the dns servers are reseted and i can connect to internet, the i add them again and everything works ...

---

### Post by LucidTaZ on 2006-09-19
My internet access is gone too. I can still access my router (10.0.0.2) and my wireless access point (10.0.0.1).

I booted into the Ubuntu version before the update and I'm typing this now there.

---

### Post by shadeone31 on 2006-09-19
well. it's not a problem with internet.
but the problem is : my atheros wifi card is no longer seen by the system.

if i use the hardware manager, i can see an "unknow" card on my mini pci, with "atheros" as manufacturer. but there's no more drivers to handle it :(

---

### Post by Didando on 2006-09-19
I had the same problem when I updated.  I rebooted and selected the previous kernel image from the list on the GRUB boot screen and all works as before.  Not sure what broke but it was probably in the restricted modules.  It affected my wireless 

 Ethernet controller: Atheros Communications, Inc. AR5211 802.11ab NIC (rev 01)

kernel module: ath_pci

Regards!
Danny

---

### Post by pccampos on 2006-09-19
The problem seens to be with the "sky2" module that was replaced with "sk98lin". But even when I load the sk98lin module the network interface doesn't shows up in my system.

How can I tell the system that sk98lin means to be eth0 or eth1?

---

### Post by elementadiobam on 2006-09-19
> **linuxNewb said:**
> After rebooting again, everything is fine -- yes I'm embarrased.

When I updated my internet access showed that I was connected to my router and everything it just didn't go to any pages. The first thing I did was reinstall ubuntu. I should have tried rebooting. I think I will try updating again later today when I have less need for the internet.

---

### Post by arg553 on 2006-09-19
I'm having the same problem with my atheros card.  

Also the update made my ati graphics card stop rendering in direct mode.

---

### Post by utopienne on 2006-09-20
I just installed Linux Monday, and have never used it before, but I thought I would add my two cents and try and help figure out the problem.. 
When I first booted, my (only) Microsoft wireless card auto-configured perfectly. (as eth0)
I updated. I think the card still worked, but I may have just shut down. 
New start-up, different location with different wireless network. I changed profiles, reconfigured from the System -> Admin -> Networking configuration tool (using DCHP) success!

New Start-up, back at home, had to reconfigure networking set-up (probably messy, because I don't know what I am doing) Had to restart, it worked. Shutdown

Thismorning, with no change, it recognized the hardware but could not actually connect to the internet, Network Monitor (in the panel) showed the SIOCGIFFLAGS error. The System -> Admin -> Network still showed the eth0 device as active (although last night it hadn't because it wasn't installed on start-up). 
Looked for solutions here, restarted and it auto-detected the correct set-up. 

A mystery, or it just needs to be restarted? I probably downloaded AFTER the fix. 

> **beanie said:**
> Hello.
I've tried the apt-get command but it seems that the command need to connect to the internet. But the problem is that my network card is not detected (caused by the latest update). So, how do I perform the apt-get update command when there is no network adapter detected? Please help. I've been stuck with Windows now...

Can you use a different computer/access point and removable storage? Of course, the important info is how to actually find the update...
Sorry no help here.

---

### Post by KLineD on 2006-09-20
I upgraded my kernel from 2.6.15-26-686 to 2.6.15-27-686. When I use -27 my wireless card is not detected by the system (it's a centrino laptop). The -26 kernel detects my wireless card and configures everything perfectly.

I'm using -26 for the time being, but I hope this gets resolved for edgy.

---

### Post by luckylucky on 2006-10-02
So I'm back from my trip and am wondering if anybody can confirm/comment if this issue has been resolved yet, or should I still avoid updating kernel?  Thanks in advance.

---

### Post by 8086ed on 2006-10-03
> **luckylucky said:**
> So I'm back from my trip and am wondering if anybody can confirm/comment if this issue has been resolved yet, or should I still avoid updating kernel?  Thanks in advance.



Dude... I posted that it was resolved 2 weeks ago.

---

### Post by JorDak on 2007-03-03
I'm a noob to Ubuntu. I thought I did something really wrong and reformated. After getting online and checking my mail via a wireless connection that just worked after the install I used the update manager. after the updates my wireless just went down. the wireless entrey in the Network settings is gone.  I still have the Ethernet connection though which still works.

---

