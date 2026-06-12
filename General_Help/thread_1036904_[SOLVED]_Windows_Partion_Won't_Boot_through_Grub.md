---
title: "[SOLVED] Windows Partion Won't Boot through Grub"
date: 2009-01-11
forum: General Help
---

### Post by theyain on 2009-01-11
I'm on my mate's tower and she has Windows installed on a SATA drive.  Well, I installed my PATA drive that has Ubu on it and then edited the grub menu.lst item so that Windows is an option from the menu.  However when I try to boot into Windows I get "Error 23: Error while parsing number"

At first I thought it was that had put in the wrong drive name or partition number (sda,0) so I put (sda,1) and still got the error.

I kept trying different things, but I still have yet to boot into Windows from grub. :(


I know that the Windows partition is sda2.  Maybe I'm missing something obvious and I'm just not seeing it.

---

### Post by caljohnsmith on 2009-01-11
All the HDDs are (hdX) to Grub, even if they are a SATA drive. How about trying this entry instead:
```
title Windows XP 
root (hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
If that doesn't work, let me know exactly what happens when you try it; also, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your Windows booting problem might be.

---

### Post by IllegalCharacter on 2009-01-11
Can you post your menu.lst file? Also keep in mind that GRUB doesn't like spaces, so things like (hd0, 1) can mess up.

---

### Post by theyain on 2009-01-12
I don't get it!

Your code for GRUB worked, while Mine did not.

Yours was:
```
title		Windows XP 
root		(hd1,1)
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

While mine was the default Debian one:
```
title		Microsoft Windows XP
root		(hd1,1)
savedefault
makeactive
chainloader	+1
```

With yours, I was able to boot.  But when I tried mine, I just got "Starting Up..."

Care to explain why yours worked and mine did not?

And don't explain it in layman's terms.  Just because I'm unfamiliar with how GRUB works and booting doesn't mean I won't understand what your saying.  And if I don't, I can do a Google search.

---

### Post by caljohnsmith on 2009-01-12
Glad to hear you can boot Windows OK now. About the mapping lines, those are to fool Windows into thinking it is being booted from the 1st boot drive or (hd0), even though Windows is actually on the 2nd boot drive or (hd1). Windows normally won't boot from anything but the first drive in the BIOS boot order, unless you modify Windows XP's boot.ini file. But fortunately Grub is sophisticated enough that it can fool Windows into thinking it is being booted from (hd0) by using that mapping technique when Windows is really on (hd1). That of course means if Windows is all ready on the first boot drive or (hd0), you can omit the mapping lines in the Grub entry. Anyway, cheers and have fun with your OSes. :)

---

### Post by theyain on 2009-01-12
Ahh, that makes sense.  Its a stupid bug, but it makes sense.

---

