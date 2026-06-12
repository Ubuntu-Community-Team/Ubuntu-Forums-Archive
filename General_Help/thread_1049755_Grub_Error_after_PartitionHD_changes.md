---
title: "Grub Error after Partition/HD changes"
date: 2009-01-24
forum: General Help
---

### Post by Rubicon421 on 2009-01-24
I changed a partition size and after rebooting, I got a grub error (22 I think) and could not get into either OS (Vista or Ubuntu). I had the same error a while ago after installing a second HD. Both times I ended up reinstalling Vista then Ubuntu. 

What exactly causes this error and what can I do to prevent it in the future if I need to make any partition or HD configuration changes?
If I installed Ubuntu on an external portable USB drive and occasionally rebooted with it disconnected would I run into the same problem or would the machine operate as if it only ever had Vista on it?

---

### Post by caljohnsmith on 2009-01-24
I think it would help to first get a clearer picture of your setup related to booting issues, so how about booting your Live CD, download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by Rubicon421 on 2009-01-24
That might help if I could get to it when the problem occors, but I have done a restore since it happened both times. But I suppose if I couldn't boot past the grub loader that the live CD would be a helpful way to get some info next time though.

---

