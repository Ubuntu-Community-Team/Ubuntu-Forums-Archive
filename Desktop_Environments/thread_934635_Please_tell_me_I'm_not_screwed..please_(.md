---
title: "Please tell me I'm not screwed..please :("
date: 2008-09-30
forum: Desktop Environments
---

### Post by caitistrophic on 2008-09-30
Please tell me I'm not screwed..please :( My ubuntu is severely messed up - when ever I boot up I have to cancel a boot scan otherwise it claims to be unable to find an OS. This has been happening ever since an update a while a back - since then I've refused to do anymore for fear of making things worse.  I'm a horrible newb. I sort of stopped caring about whether this ubuntu works as long as it can survive until I can just reinstall the whole thing all over again - maybe even try a different version.  I'm pretty sure I need to but - I have to wait one more week before I have the capability of backing up all my stuff. I have a ton of important paper work, family pics and ebooks on here.  Losing any of it would be the end of me - I'm probablly over reacting because of the emotional attachment - it's hard to do anything when I keep crying - it's so stupid.  But here's what's going on. My panels are gone and I can't access the terminal to reinstall what I need for it. I've already read so much that doesn't seem to apply here because so much on this system doesn't work I don't even have help files on here and I don't know why - anyways, the panels are gone gone - I uninstalled them somehow while trying to get rid of evolution the mail client thingy.  It said the desktop and panels were attached to one of evolution things I uninstalled - I just assumed that they were just parts of the panel and desktop - or had hoped - but it didn't turn out that way - they're all completely gone. Something with evolution keeps running my processes everytime I let my son play on here and it scares me that my pc is gonna burn out like he did to my last pc.  I lost so much back then and I can't go through that again.  He plays on sesame street and disney go alot (he's five) and I don't know - I hate those sites anyways but he loves them. And everytime he's been on there the cache fills up and the only way I I know how to dump it all is from opening the gimp on my part of the pc - there's about 2000 brushes in it so it takes up enough cpu to dump all of the cache usually.  But it didn't work yesterday and I looked at the system monitor and evolution exchange storage - I think that's the one - was way using up a lot of cpu so I killed the process and everything was okay. But it did it again today and I got frustrated and uninstalled the evolution stuff hoping it wouldn't be a problem anymore.  I can't figure out any short cuts to open the terminal so that I can sudo apt-get gnome (I'm assuming that's what I need to do to get my desktop back and my panels back) but I can't get terminal open. I even tried right clicking on a file for the open file with this thingy - there's that part you can type a command into, but it didn't work.  I guess it's not really a terminal. Does anyone know where I can find the actual file to open the terminal or if there is really a hotkey for it already set up? Or am I really just screwed?I don't even know if I'm asking the right questions or anything. If anyone can help I'd really really really appreciate it so much.

---

### Post by Therion on 2008-09-30
Okay, calm down and tell me what happens when you boot up.  Nothing more, really... JUST what happens when you try to boot your computer.  How far can you get, what do you see?

---

### Post by caitistrophic on 2008-09-30
First it shows me the pc logo and gives me the options of showing the boot screen and bios. 
Then it loads to the list of OS's I have to choose from, there's like 3 or 4 different versions of ubuntu because of updates on the list. And they all load the same it seems so I always pick the latest one. Which is like 19 or something - I'm always loading while cleaning my desk and refilling the bird food dishes so I haven't really paid much attention until now. I could go back and write it all down if it would help.
After I press enter to load the OS it goes to the ubuntu loading screen where it says it needs to perform a scan - whenever I let it scan it gives me a huge list of things it can't find says there's no OS and then sits on a root command line. But if I hit esc when the scan starts it stops and the OS loads with no problems to teh login in screen and from there it always logs in just fine.
When I first installed ubuntu it worked fine until I let it do the updates. Once it even reinstalled firefox on me and removed my bookmarks.  Since then and since the additional OS names (all say ubuntu but have diff numbers) I've stopped doing the updates out of fear of loosing any of my files.

---

### Post by Therion on 2008-09-30
Okay... That's cool.  Thank you.

First, let's try and get your desktop back.  

I want you to reboot and break out of the disc scan so you can log in.  Do that and let me know what you see from there.  

We're going to try and reset your desktop if your panels and such are missing.

---

### Post by caitistrophic on 2008-09-30
After logging in everything is normal looking but the panels being gone. My wallpaper I set is still there, and the folders on the desktop are still there.

---

### Post by mike1234 on 2008-09-30
This will restore gnome to it's original settings: Drop to a terminal by hitting CTRL + ALT + F1, login to your account, and run this command:
rm -rf .gnome .gnome2 .gconf .gconfd .metacity

Get back to your GUI desktop by hitting CTRL + ALT + F7.

Just like the first time you ever logged into your Gnome desktop.

M.

---

### Post by Therion on 2008-09-30
Okay, this is sounding good.  I'm not sure how far I can take you regarding your data recovery, but if you can get to your desktop you *should* be in good shape.  It sounds like you've just deleted your Gnome panels, so lets reset things and get them back.

I want you to open a terminal:  **CTRL+ALT+F1**
Then Cut and Paste in this command line into the terminal and press Enter:
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```
Now, this is the dreaded (!!) "rm -rf" command.  If anyone want's argue that this is a valid use of this command, bring it on.  

What this is going to do is delete your existing .gnome, .gnome2, .gconf, .gconfd and .metacity folders from your system.  That's it.  Those folders contain the config files that I believe you've screwed up.  So we're removing them so when you log back in, they will be recreated in their default configuration.

Do that by pressing: **CTRL+ALT+F7**

And *voila!*  Your Gnome panels should return.

---

### Post by mike1234 on 2008-09-30
You mean invalid? :) I'm sure someone will say something. But glad you pointed that out. It is a concern sometimes but not in this case. I have used this command a few times when gnome ran amok.

M.

---

### Post by caitistrophic on 2008-09-30
When I use CTRL+ALT+F1  this comes up - 
four numbers with a lot of fives in it- a dot -and the six more numbers followed by this message "powernow-k8:failing targ, change pending bit set  --- that's the message that has been comming up ever since the updates. That's a ton of the messages that come up after the scan if I let it scan - what does it mean? Should have gotten help for this sooner?

---

### Post by Therion on 2008-09-30
> **mike1234 said:**
> You mean invalid? :) I'm sure someone will say something. But glad you pointed that out. It is a concern sometimes but not in this case. I have used this command a few times when gnome ran amok.

M.
If anyone wants to argue that it's a valid (i.e. a "good") usage.  Which we're both agreeing, it's not.

---

### Post by caitistrophic on 2008-09-30
> **caitistrophic said:**
> When I use CTRL+ALT+F1  this comes up - 
four numbers with a lot of fives in it- a dot -and the six more numbers followed by this message "powernow-k8:failing targ, change pending bit set  --- that's the message that has been comming up ever since the updates. That's a ton of the messages that come up after the scan if I let it scan - what does it mean? Should have gotten help for this sooner?

I don't know if I was clear or not - that message repeats itself with a bunch of different numbers - like it floods the screen with it and doesn't ever stop. I leave to go smoke a ciggarette and come back and it's still going.

---

### Post by mike1234 on 2008-09-30
> **caitistrophic said:**
> When I use CTRL+ALT+F1  this comes up - 
four numbers with a lot of fives in it- a dot -and the six more numbers followed by this message "powernow-k8:failing targ, change pending bit set  --- that's the message that has been comming up ever since the updates. That's a ton of the messages that come up after the scan if I let it scan - what does it mean? Should have gotten help for this sooner?


It's a bug.  First reboot your computer and go into bios and look under settings to see if you have a feature called "Cool 'n' Quiet". Then disable it, save, exit and reboot. Unfortunately it seems to be a problem with linux kernel. This happened after updating right?

M.

---

### Post by mike1234 on 2008-09-30
You can also try rebooting your computer, as it's booting up press esc key, select the kernel that's the lower value. Highlight and hit enter. It sounds like your latest kernel update is causing problems from what I have read.  Rolling back the kernel to a previous version should resolve this. And then you can remove the new kernel later. Because it will always try to load the latest version. 

M.

---

### Post by caitistrophic on 2008-09-30
I changed the fan setting and rebooted a few times trying other kernels and everytime I type ctl+alt+f1 it does the same thing, although the numbers changed, but they still say' "powernow-k8:failing targ, change pending bit set".  The fan settings weren't titled "cool 'n' quiet" but were still there to be edited to disabled - the fan is louder now that's the only change. Was it the right thing to do or did I miss understand something? I'm so sorry this is being such a pain in the @ss. :(

---

### Post by Therion on 2008-09-30
Okay, the problem here lies with your AMD processor... Your CPU.  The error is due to a hardware bug with some AMD processors.

The problem can be solved by using the Terminal and simply disabling the "check" that Ubuntu is doing that is resulting in the error, but you can't get INto the Terminal.

I'm sorry, but at this point I don't know what to tell you.  I can tell you that, most likely, your data IS safely stored on your hard drive.  You just can't get to it yet.  Proceed with caution.  

You MIGHT be able to boot from a LiveCD and copy your data over to something else.  If you can, I would.  Copy it to a USB thumb drive, your iPod whatever you can.  If you don't HAVE a USB thumb drive or an iPod, I'd go GET one, assuming all this stuff is as valuable as you say it is to you.  Then of course you will MAKE BACKUPS.

Then hope someone comes along who can help you work this out properly.

---

### Post by caitistrophic on 2008-09-30
I can access my regular files, I've been getting my browser open by opening one of my notes in it. I've got some stuff backed up, just no room for anymore until Friday - I'm getting a huge external that will be able to back everything up and I'll be doing that more regularly. 

I think I just need to get help sooner when something goes wrong. I've been focusing on work so much and I'm not really good at asking for help - sort of a pride issue but mostly an embarassment issue. I've known a lot of rude people not really willing to help that's made it harder to ask and I'm working on that. You guys have been really nice and helpful and I'll be around more frequently when I do a fresh install to make sure I do things right next time. Thank you for taking the time it's taken to talk me through all this. Atleast I'm not in danger of loosing any files - that's always my biggest fear. Just gotta wait 'till pay day for the external now.

---

### Post by mike1234 on 2008-09-30
Don't be afraid to ask. Those who are rude or unwilling to help aren't worth talking to anyway. Hopefully you get this resolved soon. Google is a great source of information too.

M.

---

### Post by caitistrophic on 2008-09-30
Yeah, seriously thank God for google. It's been a big help in the past, I just need to work on the problems sooner before they add up.  Thank you a ton for the encouragement it really is helpful.

---

### Post by niaz2 on 2008-10-01
thanks to you .this is so fine. 
i really do this.

---

