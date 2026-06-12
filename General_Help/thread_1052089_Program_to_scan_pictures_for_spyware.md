---
title: "Program to scan pictures for spyware?"
date: 2009-01-27
forum: General Help
---

### Post by Camilia on 2009-01-27
I would like to add a program to scan pictures I copy for spyware. Is there 1?

---

### Post by sdennie on 2009-01-27
As long as the pictures are normal pictures (.jpg, .gif, etc.) and not executables, they cannot contain spyware.

---

### Post by hyperdude111 on 2009-01-27
As above, but it is also very unlikely to come across linux spyware, maybe as a firefox addon of hole but not specifically for linux

---

### Post by Camilia on 2009-01-27
I have a hard time believing that spyware can not come in through pictures, for I got trojan malware from copying picture previously. If I am wrong humor me and provide me with the name of a program to scan data, please.

---

### Post by snova on 2009-01-27
> **Camilia said:**
> I have a hard time believing that spyware can not come in through pictures,

Believe it. ;) It is simply not possible. What would an image be able to do? They don't contain any executable code. They wouldn't even be valid executables.

> for I got trojan malware from copying picture previously.

Then it wasn't an image. Either it was an executable masquerading as an image (.png.exe, for example) or you got it elsewhere.

> If I am wrong humor me and provide me with the name of a program to scan data, please.

Perhaps ClamAV? I wouldn't really know...

---

### Post by jgoguen on 2009-01-27
> **Camilia said:**
> I have a hard time believing that spyware can not come in through pictures, for I got trojan malware from copying picture previously.
Do you mean "got" as in "the executable code for the trojan was physically on the computer" or "got" as in "the trojan infected the computer"?  The first is possible (and I use "possible" loosely), the other isn't.  However, I wouldn't go forwarding the picture to your Windows-using friends :)

> **Camilia said:**
> If I am wrong humor me and provide me with the name of a program to scan data, please.
ClamAV.

---

### Post by Camilia on 2009-01-27
When I was using windows os it happened. I was copying pictures to use for avatars at forums.

---

### Post by jgoguen on 2009-01-27
Windows doesn't function the same way Ubuntu does.  A virus that infects you on Windows before you even know it won't get anywhere on Ubuntu.  Even using WINE, Windows viruses function very poorly, or more likely completely fail to function at all.  ClamAV will scan for viruses, but "virus found" doesn't mean "system infected".  It means "a virus was found in the specified file".

---

### Post by hansdown on 2009-01-27
> **Camilia said:**
> When I was using windows os it happened. I was copying pictures to use for avatars at forums.

Something similar to this?

[http://www.spywarehunter.org/entry/my-best-photos-is-trojan-horse/](http://www.spywarehunter.org/entry/my-best-photos-is-trojan-horse/)

---

### Post by Camilia on 2009-01-27
> **hansdown said:**
> Something similar to this?

[http://www.spywarehunter.org/entry/my-best-photos-is-trojan-horse/](http://www.spywarehunter.org/entry/my-best-photos-is-trojan-horse/)

Now I am uncertain what to do for read at the link:
Sophos claims the executable file to be a Trojan horse, which has been developed to download more pernicious code from the internet, but poses itself as a JPG graphic by making use of a dual extension and interleaving manifold spaces into the filename.

---

### Post by hansdown on 2009-01-27
> **Camilia said:**
> Now I am uncertain what to do for read at the link:
Sophos claims the executable file to be a Trojan horse, which has been developed to download more pernicious code from the internet, but poses itself as a JPG graphic by making use of a dual extension and interleaving manifold spaces into the filename.

It only works with windows machines. I love ubuntu.

---

### Post by snova on 2009-01-27
> **Camilia said:**
> Now I am uncertain what to do for read at the link:
Sophos claims the executable file to be a Trojan horse, which has been developed to download more pernicious code from the internet, but poses itself as a JPG graphic by making use of a dual extension and interleaving manifold spaces into the filename.

It means the file simply has two extensions, **.jpg.exe**. It's not an image at all, it's a program. It just has a filename that makes it appear to be an image, since Windows will hide the .exe part.

---

### Post by hansdown on 2009-01-27
Just install clamav from the synaptic package manager Camilia.

---

### Post by druellan on 2009-01-27
Mmmm, lets see if we can make this clear.
Is *possible* for a spyware to exist on a JPG/PNG, besides, you can't get infected displaying or copying the file *BUT* since Windows by default did not show file extensions, some spyware can disguise as images but they are in fact fully executable files and NOT real JPG files.
In short, a Spyware is not likely to exist on a image file, but a file looking like an image can be in fact a spyware.

About anti-spyware software for Ubuntu/linux, there are none, just because (still) linux did not have any spyware/virus to worry about.

---

### Post by 2hot6ft2 on 2009-01-27
> **Camilia said:**
> I would like to add a program to scan pictures I copy for spyware. Is there 1?
I don't know about anti spyware for linux. Here are some options for anti virus. I remember reading something about injecting .TIFF pics with code but don't have the link off hand, I think that's what you're talking about.

Linux doesn't really need an anti virus (see here [https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)) but it is installed by default anyway. If you want a gui for it use this in a terminal
Applications>Accessories>Terminal
```
sudo apt-get install clamtk
```
then it will be in
Applications>System Tools>Virus Scanner

If you want avast or AVG look here. [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

Avast and AVG only have 32 bit versions.

And to add avast to the menu the instructions are here. [http://forum.avast.com/index.php?topic=34748.0](http://forum.avast.com/index.php?topic=34748.0)

---

### Post by bodhi.zazen on 2009-01-27
It is possible to "hide" malware in files that appear to be picture files in that they end in .jpg

These attacks are quite sophisticated and I am not aware of any tool in linux to test such files.

Most of these things are targeted at windows, although I did once see PHP code inbedded in a .jpg. That example was "spyware" in that it examined your cookies in your browser.

There are not tools in Linux because linux is not windows and such things do not automatically run on Linux.

See : [http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

If you use windows, use the windows antivirus / anti spyware tools.

That is not the same thing as telling you to ignore security in Linux, it is just that security is different and you have to change your mentality away from the winsows scanning tools. See the stickies in the Security forums.

---

### Post by Camilia on 2009-01-28
I read that clamav scans for viruses but doesn't remove them. 

Rkhunter seams to just scan too but doesn't remove them.

For some reason I don't see the icons to thank everyone. Also don't see in thread tools mark thread solved.

---

### Post by Mud.Knee.Havoc on 2009-01-28
You don't need ClamAV to remove the virus, since Windows viruses don't really work in linux. (*There is always considerable debate as to whether Windows viruses can be run in wine - it seems that it is possible, but nothing will happen most of the time, as wine lacks most of the stuff that viruses need to operate properly).

So if ClamAV detects a file with a virus, just delete the file.  It's not like Windows, where you'll realize you have an infected system and need to try to repair dozens or hundreds of infected files.  It'll just be some file with a virus that you haven't (and most likely can't) run yet.

---

### Post by Mud.Knee.Havoc on 2009-01-28
> **Camilia said:**
> Now I am uncertain what to do for read at the link:
Sophos claims the executable file to be a Trojan horse, which has been developed to download more pernicious code from the internet, but poses itself as a JPG graphic by making use of a dual extension and interleaving manifold spaces into the filename.

What kind of file would this be?  THIS-IS-NOT-A-VIRUS-OR-IS-IT.DOC.GIF.PDF.ISO.AVI.BMP.JPG.TXT.EXE

I'd stay away from it, as it's only the final .xxx that counts - in this case, a .EXE. Everything else is part of the filename, not the extension.

---

### Post by Camilia on 2009-01-28
Great info!!\\:D/ Now I feel very confident that I have no viruses on my computer, which has only Ubuntu os.

I downloaded via the synapse clamav. So nothing showing I had it so went to the terminal and pasted sudo apt-get install clamtk. Now I can scan my pictures.

---

### Post by duds2008 on 2009-02-06
lol @ mud

---

### Post by Camilia on 2009-02-06
> **duds2008 said:**
> lol @ mud

Yeh, I am still a little paranoid. 1 day I will take time to read info on why ubuntu is more secure than windows. 

Love clamav!!

---

