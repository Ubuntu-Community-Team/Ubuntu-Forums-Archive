---
title: "can't enable &quot;costom&quot; visual effects. HELP!"
date: 2008-02-06
forum: Desktop Effects &amp; Customization
---

### Post by Shaun440 on 2008-02-06
HI

When i go into the visual effects tab, and try to select anything other than "none", the windows goes grey for about 20 second, then reverts back to none, no error messages or anything. 

I have nvidia drivers installed, and compiz was actually working fine earlier today, but just before, after changing a setting, the computer froze for about a minute, then reverted back to "none" under visual effect and now i cant change it back.

HELP

p.s I'm a noob to linux

---

### Post by K.Mandla on 2008-02-06
Can you tell us more about the machine? System specifications or hardware?

Do you remember what setting you changed?

---

### Post by Shaun440 on 2008-02-06
8800gts 512
Q6600
2gb ram
ubuntu 7.10

I think i changed from using "cube gears" to "cube atlantis"

---

### Post by vikasvishnu on 2008-02-06
I think your current compiz settings profile got corrupted due to some reason. Just try renaming the compiz folder in your Home directory to some other name and restaring your X? The folder should be hiddent under your Home Directory with the name .compiz rename that to something like  .compiz_backup and restart your X by pressing Ctrl+Alt+Blackspace. This should do no harm but it will create a new profile under your Home folder with the name .compiz. 

Could you give it a try and let us know your findings?

---

### Post by ii bk ll on 2008-04-30
Hi I am having the same problem but I dont understand your instructions in the post before me... Pretty new to linux so if any one could help me it would be greatly appreciated!!!

---

### Post by King_Critter on 2008-04-30
> **ii bk ll said:**
> Hi I am having the same problem but I dont understand your instructions in the post before me... Pretty new to linux so if any one could help me it would be greatly appreciated!!!


1. Open your home folder

2. Click View (on the toolbar at the top of the window) and then click Show Hidden Files (or something like that). Alternatively, you could use the keyboard shortcut Ctrl+H.

3. Whichever way you do the above, a bunch of folders and files will appear, all of them starting with a period (.). These are configuration files. Find he folder called .compiz and either delete it or rename it. This will remove all your custom settings. Log out, then log in again and try to do whatever you were trying to do. It should work now.

---

### Post by vikasvishnu on 2008-04-30
> **ii bk ll said:**
> Hi I am having the same problem but I dont understand your instructions in the post before me... Pretty new to linux so if any one could help me it would be greatly appreciated!!!

Whatever, King_Critter mentioned is perfectly correct. The Compiz user settings are stored under a folder called .compiz in the users Home directory. Using a Ctrl+H shall un-hide those folders. Removing it, restarting your X Display (Logging out and logging in) should create a new profile in your Home directory solving your issue.. 

Also if you are using the latest Ubuntu Version, Hardy Heron, please note that the .compiz folder will be present under another folder in your Home directory called .config

full path is ~user/.config/.compiz

So if you are using Hardy Heron version, this is the folder which needs to be removed.

Hope that helps. 

Vikas

---

### Post by ii bk ll on 2008-04-30
Thanks for your help so quickly

I deleted the compiz config file but I am still running into the same issue, I cant change any settings. For a while it was running on normal effects but then I installed compiz and now i cant change it at all. I have been doing research for this problem and I am sorta thinking its because I am running on   a Macbook. I read that my video card is blacklisted so I followed some instructions to try and fix that and still no luck. I followed another set of directions for compiz on the Macbook and now my screen is in horrible resolution and I cant change it. I am pretty much out of luck for getting compiz on my computer and now I have to retrace my steps to get my screen in the correct resolution......](*,)](*,)

---

