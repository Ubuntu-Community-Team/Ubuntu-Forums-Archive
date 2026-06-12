---
title: "Ubuntu Slow startup and hibernation problems."
date: 2009-05-14
forum: General Help
---

### Post by chrisbay90 on 2009-05-14
Hi,

I am running Ubuntu 9.04 alongside windows XP dual booting between them.

I only just started using ubuntu (or linux at all) its been a lot better then i anticipated i just have a few very small 'problems'

[SIZE=2]**Slow startup.**[/SIZE]

After I select [SIZE=1]Ubuntu[/SIZE] from the boot menu the screen reads
> 
Boot from (hd0.4) ext4    670400836-8ccc-4891-4891-b0ef-507e14ab86661
Starting up ...  
_And stays like that for 10 or so seconds, then once it finally gets to the loading screen the bar bounces around a few times before beginning to actually start up.

It's not really much of a problem as it still starts up without any errors and doesn't slow me down that much. However I had the same version of Ubuntu installed on the '*same*' partition on the same laptop and this did not happen.

I tried resizing the partitions which stopped my last install from booting, having only installed it 1 day ago there was nothing worth saving so I just completely reinstalled Ubuntu. This time however I changed the partition to an extension partition and created to logical partition inside that one for ubuntu one for swap.

Could this be whats slowing things down? The thing is i have to do this as my laptop comes set up with windows installed across 3 partitions, so i can only create one more partition and im not just ready to use ubuntu exclusively.

[SIZE=2]**Hibernation errors.**[/SIZE]

when I hibernate my system, ubuntu displays the following:
> 
[   183.5078698] MMC: killing requests for dead queue
[   183.508849] btusb_intr_complete: hc10 urb f6383400 failed to resubmit (1)
[   183.508849] btusb_intr_complete: hc10 urb f6383400 failed to resubmit (2)
[   183.508849] btusb_intr_complete: hc10 urb f6383400 failed to resubmit (4)
This might not be EXACTLY what is displayed, i wrote it down bby hand in a hurry.

Again this isn't a major problem as it successfully hibernates and resumes in the end, although im assuming getting those error messages isnt normal.




Any help would be appreciated, thanx in advance.

---

### Post by chrisbay90 on 2009-05-26
bump

---

### Post by sean_worker on 2009-05-29
my start up is fine, though only my /home is on an extended partition

I get the "MMC: killing requests for dead queue" when I hibernate ... which turns out not to hibernate anything because when restarted it just boots into a fresh session

---

