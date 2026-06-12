---
title: "ubuntu-5.10-install-i386.iso"
date: 2006-01-06
forum: Desktop Environments
---

### Post by LanceM on 2006-01-06
I have downloaded the iso images three different times from three different mirrors and created a cd from each image. I burned the first copy at 16x, the second at 8x, and the third at 4x. I can boot to each cd and start the install of Ubuntu, but I keep getting file access errors on the cds and the installer tells me that the cds are corrupt.

I was thinking that I might have a problem with  my burner but I burned Fedora Core 4 and installed it with no problems.

I am not sure what to do from here so any suggestions would be great.

Thanks,
Lance

---

### Post by byen on 2006-01-06
i would have to say it might be one of the two below
1. corrupt downloaded cd iso
2. Bad Cd Burn Process

For 1:first after downloading the ISO make sure that yu check the integrity of the ISo by using a program like this:
[http://www.nullriver.com/index/products/winmd5sum](http://www.nullriver.com/index/products/winmd5sum)
(free and secure)
now...after doing this Go to [www.downloads.com](www.downloads.com) and search for the program "deepburner". its free and was developed by the developers with ISO burning in mind. It is really good and damn easy to use. Download it and burn the cd as an ISO project at a slower speed. Let me know if you have any probs. I might have some alternatives.
Goodluck and Welcome to Ubuntu.

---

### Post by LanceM on 2006-01-06
winmd5sum showed a good iso image. I used deepburner and 4x and created an install cd. I am still getting the same error.

---

### Post by byen on 2006-01-06
If you hadnt metioned the fact that it shows that the cds are corrupt. I would have suggested you to install with no-acpi option and to turn off usb legacy support (in boot options) off. But I am kinda bummed here..  Sometimes certain hardware (hdd) have compatbility issues but im not really convinced yet that this is the case here....
so " cds are corrupt." is the only error you get? even after the new burn?

---

### Post by LanceM on 2006-01-06
I can boot to the cd and go through the language, location, and keyboard selection, detects hardware, scans cd-rom, then fails loading installer components from cd with this message: Failed to copy file from CD. Retry?

At that point I run check cd integrity and I get a failure on MD5 checksum.

---

### Post by byen on 2006-01-06
> At that point I run check cd integrity and I get a failure on MD5 checksum. 
Meaning ...either the download is corrupted or the cd write. Did you match your md5 checksum that you got from the cd to the one given on the site from which you have downloaded?

---

### Post by LanceM on 2006-01-06
I did and it matched. The odd thing is that I was able to burn Fedora Core cds and they worked great. I am downloading Ubuntu 5.04 right now to see if I get the same problem with a different version.

---

### Post by LanceM on 2006-01-06
I think I figured it out. The installer does not like my DVD/RW. I swapped my drives so the cdrw would be the boot drive and Ubuntu is installing now. Thank you for your help.

---

