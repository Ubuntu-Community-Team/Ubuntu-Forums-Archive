---
title: "Dell XPS 720 installation problem(s)"
date: 2007-09-04
forum: Dell  Ubuntu Support
---

### Post by Mitush on 2007-09-04
I have been using Ubuntu for 1.5 years now. Have old Breezy Badger box as well as several Dapper Drake boxes. I recently got the new Dell XPS 720 (with Nvidia 8800 GTX) and trying to install Ubuntu on it. I have dapper installation CDs from one year ago (6.06.1, both desktop and alternate) which I tried to use for installation. I got the IO-APIC kernel error at first, which I was able to fix by F6, and adding noapic just before '--' at the end of the boot options line.

But after that the desktop CD could not install/configure the X server stuff (gave me console instead of the ubuntu desktop), so I tried to use the text-based installation from the alternate CD. There was a problem there as well, namely, it did not find network interface, so I canceled installation after that.

So, it looks like I cannot install the dapper on my new box. Is it possible that the new 6.06.1 download from ubuntu website could fix my problem? Do they update those .iso files so that it makes sense for me to try to download the "current version"?

I prefer to install dapper because it will be supported longer than 7.04. However, I am downloading 7.04 now, just to see if it will work for me.

---

### Post by Afishionado on 2007-09-04
My two cents: Life is a lot nicer if you stick with the most recent version (in this case, 7.04). Random software off the Internet is more likely to work, and you'll have more / better drivers. Besides, Ubuntu is really easy to upgrade as operating systems go. You can upgrade in place fairly well without trashing your files and settings.

Re your actual problem, can you tell us anything about your network setup? What network card you have? Are you on DHCP? (If you don't know, then probably yes.)

---

### Post by Mitush on 2007-09-05
After downloading I tried 7.04 and it worked. I did't even have to do the noapic option.

---

### Post by rek2 on 2007-12-19
I just got the XPS 720 yesterday and is awesome!!
but I have try to book K/ubuntu on it with no success..
like the kernel will load but not X... 
my question is.. did any of you had to do anything special to 
make it work with gutsy?


Thanks

---

