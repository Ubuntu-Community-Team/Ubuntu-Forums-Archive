---
title: "re-sized partitions.. now won't boot :/"
date: 2005-03-02
forum: Desktop Environments
---

### Post by SurreaL on 2005-03-02
hello everyone!

I have XP Pro along with Ubuntu dual booting on my Toshiba laptop, and so far things were going pretty good. I've fiddled around with the system enough so that it is now set up just the way I like it. The only problem was in the original partitioning, I had given XP 9 gigs, and Ubuntu 5, but after seeing how much I use Ubuntu and haven't even booted to Windows ever since.. Well I decided to resize the partition (in windows using partition magic, since that's the only way I knew how at the time)

This broke everything :P Afterwards, neither windows NOR linux would boot.. windows would freeze in the loading animation before showing the login screen, and linux just shows a "Cannot load from harddisk. Insert Systemdisk and press any key." message. I managed to get Windows back simply by booting into safe mode and then rebooting.. but I have no idea how to fix Ubuntu.

Does anyone have any pointers? I'd like to avoid re-installing Ubuntu yet again if at all possible, lol. I was just getting to like how I had everything set up with all my window managers, etc :)

TIA
-SurreaL

---

### Post by rosslaird on 2005-03-02
Ouch.
Re-sizing partitions (either in Win or Lin) is always fraught with trouble. Probably something (like your Master Boot Record) has been modified or re-written, but I'm no expert on this type of thing.

What you could do is backup your home directory in Ubuntu (to a CD, for example, or using rsync if you have a newtork -- I wrote a tutorial about this method in the Howto section of this forum), then re-install ubuntu onto the whole hard disk (you're not using Windows anyway, right?...). Once Ubuntu is up and running again, and you have reinstalled all your WM packages, copy back your home directory. This will preserve all the settings.

Or, there may be an easier way if someone around here is a "disk-crapped-out" expert.

---

### Post by SurreaL on 2005-03-02
Thank you for your response :) I think you're probably right.. backing up my home folder and then just scrapping the whole thing might very well be in order.. I'm still a little hesitant to do that without trying SOMETHING first :) I have a funny feeling it's grub that's having a problem, so I'm sort of wondering if maybe re-installing grub will somehow fix it. Worse comes to worse it can't boot, right :P (lol)

Let's see.. I think I had a knoppix cd around here somewhere..

---

### Post by landotter on 2005-03-02
[QUOTE=SurreaL]Thank you for your response :) I think you're probably right.. backing up my home folder and then just scrapping the whole thing might very well be in order.. I'm still a little hesitant to do that without trying SOMETHING first :) I have a funny feeling it's grub that's having a problem, so I'm sort of wondering if maybe re-installing grub will somehow fix it. Worse comes to worse it can't boot, right :P (lol)

Let's see.. I think I had a knoppix cd around here somewhere..[/QUOTE]

I really doubt it's grub--sounds like you did a number to your disks. :(

You should be able to grab all relevant info with a live CD, so you're pretty much in the clear.

When you make your new partitions with Partition magic, think about making a rather large seperate fat32 partition for big stuff like media. Both Ubuntu and Windows will be able to read/write to it.

Consider this an opportunity. :)

---

### Post by SurreaL on 2005-03-02
well.. It's possible.. but I think only the boot sector of the linux partition is screwed up. (Or I suppose possibly the partition table in the MBR for the second partition) I only say this because Windows can boot fine, and therefore the boot sector of the first partition is ok. I use 'bootpart' to chainload from NT's bootloader into Grub, and it seems that it is grub which is unable to be loaded. This could be a result of 'bootpart' not taking into account the change in partition size, however I don't think so, because when I run the command in windows it prints the accurate updated partition sizing information.

This is why I think it's grub that's toasted :) (or again, the boot sector of the second partition) and so.. I haven't given up yet :D Either way you are right, this is certainly an opportunity.. for learning, at the very least! I am unfamiliar with manually setting up Grub, and this is my chance for that, hehe. The whole re-install idea will remain plan b for now.. until I have exhausted my other possibilities. A friend of mine has also suggested the [System Rescue CD](http://freshmeat.net/projects/systemrescuecd/), which I may take a look at once I get home from work and have access to my blank cd's!

---

### Post by SurreaL on 2005-03-02
Alrighty.. decided to hack away a little more, and found [this](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html) link which shows how to install GRUB manually.. In doing so, I believe I have at the very least gotten my system back into linux.. (Yay!) 

However that being said, it seems to have completely overwritten the MBR (even though I had told it to write stage 1 to the second partition, the linux one, not the actual MBR) so now, GRUB comes up first at boot time, instead of XP's boot loader. This isn't necessarily a bad thing :) I would have preferred it that way originally actually, I had just gone the other route after I found that installing Ubuntu on my desktop left XP unable to boot. Now however, it seems that both systems are booting fine.. so I got rid of the option to boot Ubuntu from XP, since Grub is now in control.. and that's it!

yay.. everything works, lol! I knew it could be fixed :D Thanks for those who offered their help, fortunately I managed to avoid a re-install after all!

---

