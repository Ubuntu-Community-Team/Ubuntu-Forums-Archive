---
title: "Xorg.conf question (resolution prob )"
date: 2008-03-02
forum: Desktop Environments
---

### Post by GrimJa on 2008-03-02
Ok, so heres basically what i need to know gentlepeeps.


with Xorg.conf / ANYTHING of the sort, be it windoze / mac / *nix.
IF you specify and INVALID resolution, it will disable that resolution for the adapter.

I've been trying like... forever to get the resolution I"m accustomed to :  (1152x864) to work with GDM, but without success.

i've edited all the relevant lines in xorg.conf. But the ONLY time I can get anything CLOSE to that res, is.. by making it virtual (which sucks).

Now, I mentioned invalied Modelines (ie. invalid res/refresh rate configs) becase.. while it is that I've specified the avtive horizontal and vertical lines + refresh rate + one other bit of info in the line - it has a few other variables that I have no clue about!


Anywho - so as to not confuse too much (which I'm sure - for someone who doesnt fool around with xorg.conf..) I have..

I need to know how to add a line to xorg.conf - that makes me use 1152x864.

(I didnt specify that I wanted to use that mode at setup which ... yeah, would have made life easier..

---

### Post by DagMan on 2008-03-02
Does your monitor and card support the resolution?

I think I remember from elsewhere that you have an nvidia card.  If so, it comes with a utility that among other things, can write an xorg.conf and set a new refresh rate which might be helpful in some circumstances.,  You need to run it with root priveleges.
First back up your xorg.conf file thoough because it writes a new one entirely on my system.

sudo nvidia settings
and in 'X server display configuration' there's selections for resolution, refresh, and if you think you can change it there, don't forget to hit apply and 'save to X coniguration file'

If you aren't liking a new file being writtten then you can aways check out the command line app 'nvidia-xconfig' which I don't know if it comes woth a man page on ubuntu because my ubuntu machine dooesnt have an nvidia card, but if not, there's one here [http://olympus.het.brown.edu/cgi-bin/man/man2html?nvidia-xconfig+1](http://olympus.het.brown.edu/cgi-bin/man/man2html?nvidia-xconfig+1)
I'm not sure if there's anything usefull there, although it does make changes by modifying xorg.conf and not overwriting it, on my distro with nvidia anyway.

You might have to install nvidia settings and nvidia-xconfig separately in Ubuntu, so don't discourage if it happens that they aren't there right away.

If none of the above helps or applies to your situation, please post you xorg.conf file
Keep in mind also that the driver in Linux might not support all the resolutions that windows does.

---

### Post by GrimJa on 2008-03-02
Why do I have the GUt feeling that my ubuntu installation (7.10) WONT have it? :| (the nvidia util)

> **DagMan said:**
> 

If none of the above helps or applies to your situation, please post you xorg.conf file
Keep in mind also that the driver in Linux might not support all the resolutions that windows does.

Thats a possibility. Could very well be.

But I have the feeling that it has something to do with those values I cant find (for my  monitor / that res!)

i used a windows utility to tell me about the active front porch and so forth, but there are some values in a line in the config file that  I HAVE NO CLUE about. And I know that If they arent right  - it wont work.

(or do I!? -thats an Idea - I"ll much around with the valid modes, and see).


But yeah, I"ll post how my xorg.conf file looks next i can.



Thanks.

---

### Post by DagMan on 2008-03-02
> **GrimJa said:**
> Why do I have the GUt feeling that my ubuntu installation (7.10) WONT have it? :| (the nvidia util)
I just had a look at my box running ubuntu 7.10
You'lle just need, if you don't have it as dependacies pulled in,
sudo apt-get install nvidia-settings nvidia-xconfig 
They're in the repos, but wheather they help is another thing.
Be sure to back up your xorg.conf, but if you really screw it up, you can always boot into the Live CD, mount the partition and copy the xorg.conf from ram to the drive, then reinstall the nvidia drivers on reboot.  I've done that before when I had to.

---

