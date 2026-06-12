---
title: "I cannot write CDs"
date: 2005-09-13
forum: Desktop Environments
---

### Post by TonyPursell on 2005-09-13
I am currently trying to write the ubuntu-5.10-preview-live-i386.iso to CD-R (although the problem exists for any iso image). I do as the Help tells me.  I right click the file, and the Write to Disc dialog appears.  My CD-RW CRX100E is selected. The write speed is 4x.  I click Write and I get the Insert blank disc message. I insert a blank disc and click Retry disc but the Insert blank disc message immediately re-appears. 

Can anyone help me?  Is it a matter of permissions somewhere?

Tony

---

### Post by Dolphin on 2005-09-13
What software is it defaulting to when you right click the file?

---

### Post by TonyPursell on 2005-09-13
I don't know what is called by the GNOME. I just right click the file, choose 'Write to Disc' from the right click menu and and the 'Write to Disc' dialog appears.  I might have a grub around and try and find where GNOME keeps this sort of information.

Tony

---

### Post by cbudden on 2005-09-13
[QUOTE=TonyPursell]I don't know what is called by the GNOME. I just right click the file, choose 'Write to Disc' from the right click menu and and the 'Write to Disc' dialog appears.  I might have a grub around and try and find where GNOME keeps this sort of information.

Tony[/QUOTE]
 Try using gnomebaker or k3b
```
 sudo apt-get install gnomebaker 
```
```
 sudo apt-get install k3b 
```

---

### Post by TonyPursell on 2005-09-14
Thanks for your suggestion, however, I would like to get the 'out of the box' solution working.  I.e the one that Help describes. I feel strongly that for Ubuntu to be a success either the built in solution should work or an alternative, like you suggest, should replace it in the default distro.

---

### Post by PhilOSparta on 2005-09-15
I had the same problem, and I agree with you that the out-of-the-box stuff should work.

Out of the box, Nautilus is the program that burns the CDs.  The fix for me:
The nautilus-cd-burner overburn checkbox had to be checked. Why? No reasons were given on a post that I found on this site.

Also, you must go to System -> Administration -> Users & Groups and give each user the priviledges for writing to CD.

 While I still have problems with Nautilus burning CDs.  Today I tried to get GnomeBaker to work.  There was an immediate crash.



Hope this helps.

Phil

---

### Post by TonyPursell on 2005-09-15
Thanks Phil, that worked. Let's hope someone closer to Ubuntu development notices this and does something about it! 

Tony

PS - I'm doing this from the live CD I was trying to burn.

---

