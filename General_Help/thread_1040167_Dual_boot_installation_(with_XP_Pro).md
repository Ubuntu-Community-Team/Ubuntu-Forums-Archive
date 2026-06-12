---
title: "Dual boot installation (with XP Pro)"
date: 2009-01-15
forum: General Help
---

### Post by snugglebugs on 2009-01-15
I was recommended to try Ubuntu. As I have a complete XP Pro sp3 installation on an Amilo Notebook, that seemed a good place to start. In the process I ran into some problems, so still don't have a working Ubuntu system:(
I downloaded ubuntu-8.10-desktop-i386 as there didn't seem to be a laptop edition. When I went to install, then I used the Dual Boot option selection box.

First, one minor one. As I don't have any CD-Rs large enough (a bit silly I think not to be able to use the standard 650MB!), I extracted the iso file to a USB memory stick and went to the install file on that.
Ubuntu install started, but told me that it was downloading all 698MB to the computer, new folder Ubuntu! As I did not want to wait around I cancelled the installation.
I then copied the memory stick to a new folder c:\Ubuntu and tried the install again from there. Same result! Started downloading all the files again. So I calmed down, went to have some food, and came back to the computer later. Annoying!

Second, I carried on with the install steps, rebooting and etc as instructed and then got to the 'choose XP or Ubuntu' options on boot. The Ubuntu logao appeared and then a loading bar with information that files were being installed.

Third, rebooting again and the choose option again so again I went to Ubuntu and a coloured screen eventually appeared and neither keyboard or mouse could make anything else happen! I checked using the choose XP option and that was OK. rebooting and choosing the Ubuntu option got the same unmoving screen and no way of getting any further.

Fourth, I searched the standard documentation and then the forums. I couldn't find anything that matched  the problems I describe, so eventually decided to try a new thread.

One point I did find mentioned that _may_ be the problem. Partitioning. I allowed Ubuntu to set a recommended partition size as I don't have any knowledge of that. I have about 27GB free space. But from a Defrag Analysis I see that scatterd in that free space there are odd files (blue lines) here and there, so I guess that the partition set is not at a boundary on the hard drive.

I tried chkdsk and defrag (via XP) several times, but those files won't shift, so **IF** that is the problem(?) what can I do?

Tony
PS As the Amilo does not have a floppy drive (so what's new!) I do not have any way of booting direct into DOS. If I could then I would have preferred to chkdsk and defrag outside of the XP environment.

---

### Post by Yashiro on 2009-01-16
- Use Hardy 8.04 Ubuntu.
- Burn it to CD. Anything else sounds like it's beyond your level of computing.
- Defrag your XP.
- BOOT FROM THE CD.
- First run Ubuntu from CD, ie do not affect your install. 
This is to see if the system will actually work. You can use the partition manager now if you want to save hassle during the real install.
- If the LiveCD experience is ok then reboot into the CD again.
- Install properly to the HD this time and pray.

---

### Post by snowpine on 2009-01-16
Hi Snugglebugs, there are two different ways to install Ubuntu. The first is to boot from a live CD and install to a separate partition on your hard drive, so you can dual boot between Ubuntu and Windows. The second is using a program called Wubi to install Ubuntu within your existing Windows partition, kind of like you would install a regular Windows application. Your post is a little confusing, but sounds like you started installing using the first method but then switched to the second method when it didn't work on the first try. I am not surprised things got messed up when you clicked cancel mid-install. :)

I would recommend that you carefully follow either 1) the regular install instructions: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) or 2) the Wubi install instructions: [http://www.ubuntu.com/getubuntu/downloadmirrors#wubi](http://www.ubuntu.com/getubuntu/downloadmirrors#wubi) and don't improvise if you get stuck--take a break and ask questions here. :) Basically what I think happened is you took a minor problem (CD capacity too low) and rather than fixing it, created bigger problems...

---

### Post by snugglebugs on 2009-01-16
See my comments in red

> **Yashiro said:**
> - Use Hardy 8.04 Ubuntu.
- Burn it to CD. Anything else sounds like it's beyond your level of computing.
[COLOR="Red"]Well, as I wrote, it seems a bit silly for the Ubuntu download not to häve been tailored to fit onto a standard 650MB CD-R. The '80min' CD is non-standard to the Philips spec.[/COLOR]

- Defrag your XP.
[COLOR="red"]Did that AND ran CHKDSK first.[/COLOR]

- BOOT FROM THE CD.
- First run Ubuntu from CD, ie do not affect your install. 
This is to see if the system will actually work. You can use the partition manager now if you want to save hassle during the real install.
- If the LiveCD experience is ok then reboot into the CD again.
[COLOR="red"]It was not my idea to download twice! The Ubuntu installer itself 'decided' to do that![/COLOR]

- Install properly to the HD this time and pray.

---

### Post by snowpine on 2009-01-16
Xubuntu (a "lighter" version of Ubuntu) will fit on a 650mb CD-R.

---

### Post by snugglebugs on 2009-01-16
See red text again

> **snowpine said:**
> Xubuntu (a "lighter" version of Ubuntu) will fit on a 650mb CD-R.
[COLOR="Red"]I simply accepted the version offered on home page of the Ubuntu website, that is, 8.10

I have found the Xubuntu 8.10 download in Europe, so I will clean out the Notebook and try that.
[/COLOR]

---

