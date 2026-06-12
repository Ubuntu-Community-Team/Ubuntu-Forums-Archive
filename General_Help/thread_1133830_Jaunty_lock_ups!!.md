---
title: "Jaunty lock ups!!"
date: 2009-04-23
forum: General Help
---

### Post by ELD on 2009-04-23
Everyday Jaunty keeps locking up on me, nothing responds no keyboard commands, the mouse stops etc etc.

It keeps doing it :(

> edit

I have a freshly installed jaunty final and it still does it, even with a different graphics card before i had nvidia now i have ati.

---

### Post by LowSky on 2009-04-23
Could you be more specific? We need more info than "its broke"

When does it lock up?
What applications do you have running?
How did you install 9.04?

BTW you have 844 Total Posts (Beans) --- not really hidden....haha
I just find this new feature so funny, as it doesn't hide it on your profile page.

---

### Post by coffeecat on 2009-04-23
Did you want to ask a question, or were you just making a statement?

I've got Jaunty on one desktop, two laptops, one netbook and one virtual machine in VirtualBox running in MacOS. Most have been running since the beta release. None have locked up on me.

So, if you want some help here, perhaps you could post some details of your hardware and setup.

---

### Post by ELD on 2009-04-23
Hardware can been seen in my signature, happens while working on php in gedit, while watching videos etc can happen at anytime, i saw other people in the jaunty forum also have a problem but now the forum is locked.

Installed jaunty via the beta cd i do beleive.

Yes i was making a statement, and since it is in the support forum obviously i would like some help finding the problem.

I don't care how many posts i have, i'm not here for a post count competition ;)

---

### Post by LowSky on 2009-04-23
I can only suggest a fresh install

as for post counts.. I just find it funny that people ar ehiding there counts but yet it is stillver yeasy to find.

---

### Post by PaulReaver on 2009-04-23
with that attitude. why dont you take take it back to the shop and ask for your money back.

---

### Post by dabl on 2009-04-23
> **ELD said:**
> 

 i would like some help finding the problem.



The problem is your system's resources are being completely consumed by something -- it's not actually locked, it just looks that way because it's too busy to respond to your mouse or keyboard.

So, what is using all the resources?  The way to find out is to run "top" in a console window, and place that window somewhere on the screen where you can keep an eye on it, and then when the system stops responding, you can look at the top window and see what process is using 100% of the CPU.  Post back with that information, and that will be the beginning of some useful help.

---

### Post by Kareeser on 2009-04-23
> **PaulReaver said:**
> with that attitude. why dont you take take it back to the shop and ask for your money back.

I don't see a need for this sort of attitude. He simply asked for help with less-than-complete details. It was not indicative of a flame.

Please be more considerate.

===

In any case, a hard lockup (no keyboard/mouse input) might be a graphics driver problem. Which driver are you using? nVIDIA came out with 180.51 recently. You can grab it on the nvidia website.

---

### Post by PaulReaver on 2009-04-23
> Did you want to ask a question, or were you just making a statement?


> since it is in the support forum obviously i would like some help finding the problem 

Looks like sarcazm to me.  I apologize if it was'nt.  Sorry

---

### Post by PaulReaver on 2009-04-23
To help with the problem though.  Jaunty final has just officially been released. would be a good idea to backup your important files and re-install the final release.

---

### Post by PaulReaver on 2009-04-23
Also I noticed that your cpu has been overclocked. Do you experience this problem with your cpu at its defaults.

---

### Post by ELD on 2009-04-23
> **PaulReaver said:**
> Also I noticed that your cpu has been overclocked. Do you experience this problem with your cpu at its defaults.

Has been fine before, left my computer on downloading for 4 hours while at work and no lock ups, problem may have gone but i will try what people have said.

---

### Post by doas777 on 2009-04-23
well first off, if your mouse won't move at all (not just slow), then it is an OS panic or a deadlock, not over-comsumption of resources. somthing is likely seriously wrong with the drivers your kernel is loading.

I have to agree with several others, try a full clean reinstall.

---

### Post by maxim99 on 2009-04-27
After searching for "jaunty lock" on google I arrive here. After uninstalling the nvidia driver that was automatically installed with my "Distribution Upgrade" procedure, so far it hasn't locked up on me.

Previously the screen would flicker a moment, usually flicker a couple of times, and then soon after it would lock up hard. I remove the driver and so far it hasn't done it anymore. I plan on reporting back after I investigate further into what driver works and such. 

After removing the latest driver, and see that after the driver removal everything worked fine, and re-installed to confirm what I was considering to be the source of the issue. I installed the driver version 180.44-0ubuntu1 and soon after rebooting I ran into a hard lock again. This confirms for me that the issue is in someway related to that driver version. Prior that that lock I had used the system for about a half hour, which is about 20 minutes more than any session I started with the 180.44-0ubuntu1 driver installed. After the hard lock I rebooted the machine and installed the next best driver which is 173.14.16-0ubuntu1 and am currently using it without any issues. It's not "recommended" but my card is old and works just fine with this driver. I will update to the next latest driver and see if anything changes.

Thank you to > **Kareeser said:**
> In any case, a hard lockup (no keyboard/mouse input) might be a graphics driver problem.

For posting this bit of information as it seems to be wholly accurate in my situation.

---

### Post by trevor_h on 2009-05-04
I had been having the same problem since upgrading from Intrepid. Removed the nVidia 180 driver and have had no problems since.

---

### Post by caryb on 2009-05-04
I upgraded my wifes laptop last Friday (1/2 way through her semester at uni) It locks up constantly when using Firefox & OOO writer it becomes totally unresponsive. The computer is a Lenovo R61 with Intel 900 graphics chip & has 2G of ram. When it locks up it writes nothing in the logs? It is using ext4 partition for / 


Cary

---

### Post by bearozo on 2009-05-04
I have lock ups as well and will try the an older nVidia driver, but seems like many has this problem with other hardware as well.

[http://ubuntuforums.org/showthread.php?t=1135055](http://ubuntuforums.org/showthread.php?t=1135055)

---

### Post by dazer26 on 2009-05-07
I'm also getting lock ups ever since I installed Jaunty.  It seems to lock up when connecting to the internet and randomly while browsing.  I'm using Kubuntu, and the lockups were happening even before I installed the 180 nvidia drivers.  It's frustrating because I don't think i'v ever had a linux distro lock up completely on me before.

---

### Post by caspar_wrede on 2009-05-10
My machine locks up too. I have an IBM thinkpad x31 with a Radeon Mobility M6 LY.

I too am using ext4 for /. maybe this is the problem?

---

### Post by ELD on 2009-05-10
I had two lockups today one as it was just loading up gnome desktop and another i tried to fullscreen vlc, both times it locked up, happend after i installed ati drivers :(

I am using ext3 so for me it won't be the ext4 problems other may have had, happens with me newer ati graphics card as well as my older nvidia one.

---

### Post by agurk on 2009-05-10
Seeing the same here. Something b0rks X. After having lockups with both nvidia 180 and 173 proprietary drivers, I've chucked them both out now to see if that helps.

---

### Post by Claus7 on 2009-05-10
Hello,

I experienced some lockups myself, and the cause I deduce was the graphics driver from synaptic. Now, having lockups both from ati and nvidia I would call it back luck. Both cards?

Could you describe exactly the system you have and the steps you have done so far?

For example, when it was the first time you faced lockups? Jaunty beta? Rc? Have you made a fresh install from there with the stable distro?

Now if you have the stable disto. How you were able to install the drivers of your graphics card? Did you remove everything before you try to do a fresh installation of the drivers? Which method did you use for the installation?

You say that you faced lockups after the installation of the ati driver. How much time did you use your distro, without the drivers installed? 

In all the above I suppose that the problem relates to the graphics card driver and their installation.
I would suggest to see what you can make out for the drivers from their manufacturers web site having in mind to avoid conflicts with previous configurations.

Regards!

---

### Post by dj-toonz on 2009-05-10
Hi all, I'm having the same problem on a 1.3gig cpu 1gig ram laptop, everything runs slow & hard drive goes nuts, then locks up on me, the only way to resolve it is by powering off & then back on, even some of the apps have started taking ages to open, Ubuntu jaunty does start up quick, it's just the everyday use of the system. the VGA graphics in the laptop is a sis graphic chip & Its set up for ext3 & not ext4, when I was using Ubuntu 8.10 I didn't get any problems. is there anything I can try to fix it. Somebody did say to try and update the kernel to a newer one, but I can't find a newer kernel in the repos :-( & it's a clean install, not a upgrade from 8.10

---

### Post by agurk on 2009-05-10
Nope, removing the nvidia drivers didn't help. I was compiling in 'safemode with networking' when it locked up again.
Every minute, there is a message showing on the screen:
[  228.707997] BUG: soft lockup - CPU#0 stuck for 61s! [collect2:3072]

I think I need to revert to ye olde 8.10.

---

### Post by PaulReaver on 2009-05-27
well its not probably not the nvidia drivers or the ext4 / partition. I use both on my nvidia mcp73 board. all good here. 

although I did notice graphical gliches (flashes) on the screen before I installed the nvidia 180 drivers.

---

### Post by macabro22 on 2009-06-02
I also keep having lock ups! I just had one a moment ago (9:53 PM now). I will post my logs

---

### Post by Claus7 on 2009-06-22
Hello,

it seems that there are not some serious problems in your files. Searching in the forums, these lock-ups do not seem to give some logs. I hope that with the kernel update (2.6.28-13) from the update manager all will be fixed. I did it today and so far so good, yet I had to reinstall the graphics drivers. Not that I faced so many lockups before though.

Regards!

---

### Post by Wiebelhaus on 2009-06-22
> **ELD said:**
> Everyday Jaunty keeps locking up on me, nothing responds no keyboard commands, the mouse stops etc etc.

It keeps doing it :(

> edit

I have a freshly installed jaunty final and it still does it, even with a different graphics card before i had nvidia now i have ati.

Run [hardware diagnostics]("http://www.ultimatebootcd.com/")

---

### Post by ELD on 2009-06-30
My hardware checks out fine and i don't have a single lock up in windows even when doing cpu, graphics etc intensive apps. If it was a hardware problem even windows would have had some problems but my XP seems to run as smooth as usual :(. I can see a lot of people it is happening to from the threads so i doubt all our hardware suddenly went bad heh.

I can confirm they still happen while not as bad as they used to be, only a few a week now!

It can happen at random times, watching a movie, surfing a forum etc.

---

### Post by alphacrucis2 on 2009-06-30
> **ELD said:**
> My hardware checks out fine and i don't have a single lock up in windows even when doing cpu, graphics etc intensive apps. If it was a hardware problem even windows would have had some problems but my XP seems to run as smooth as usual :(. I can see a lot of people it is happening to from the threads so i doubt all our hardware suddenly went bad heh.

I can confirm they still happen while not as bad as they used to be, only a few a week now!

It can happen at random times, watching a movie, surfing a forum etc.

Have you tried ATI's latest drivers. Catalyst 9.6 version of fglrx is available from AMD/ATI's website.

---

### Post by ELD on 2009-06-30
Indeed i have tried both 9.5 and 9.6, nvidia users have problems also so i doubt it is graphics related.

---

### Post by alphacrucis2 on 2009-06-30
> **ELD said:**
> Indeed i have tried both 9.5 and 9.6, nvidia users have problems also so i doubt it is graphics related.

Ok Catalyst 9.5 fixed some problems for me but I haven't suffered any lockups either before or after updating the graphics drivers. Is there perhaps some other issue that is common. Maybe motherboard?

---

### Post by phr33k-dc on 2009-06-30
i have the nvidia 180 driver version installed. someone above mentioned the 181 version is just released. how do i install it as it is siad to stop the lock-ups.
cheers in advance

---

### Post by ELD on 2009-07-01
For nividia have you tried google?
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Wasn't hard my friend :)

---

