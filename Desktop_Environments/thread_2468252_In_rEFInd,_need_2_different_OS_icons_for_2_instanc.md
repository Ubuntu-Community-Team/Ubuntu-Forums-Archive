---
title: "In rEFInd, need 2 different OS icons for 2 instances of same OS"
date: 2021-10-22
forum: Desktop Environments
---

### Post by watchpocket on 2021-10-22
***SOLVED:  See bottom of this post.***


I have an Ubuntu-MATE 20.04 LTS install (kernel 5.11.0) on an  internal nvme0 drive. 

I have another MATE 20.04 install (kernel 5.4.0) on an  internal SSD (2.5-inch), as a backup OS to the main 20.04 that's on the  nvme0 drive.

 In rEFInd (0.13.2), I've put into rEFInd's *"myicons"* directory the green-circle MATE icon, and named it "os_ubuntu.png", to match and replace the vanilla-Ubuntu ***red***-circle icon that has same name and which is in rEFInd's *"icons"* directory, per the advice of the **"Setting OS Icons"** section of the rEFInd website.

 At the moment (while I'm still in the process of setting up rEFInd) I  have just two visible OS icon "tags" (as they are called in rEFInd) showing on the rEFInd menu, one for each  of the two MATE installs. (For now, I've set to "hidden" a mess of other  OS tags that I'll need to sort through later.)

 My problem is that those two icon-tags have the same icon, and I'd like to  have a different icon representing the install on the SSD, to easily and  visually distinguish between the two OS instances, even though they're  the same OS.


 Per the further advice (in the first bulleted paragraph) on the rEFInd website under **"Setting OS Icons"** on the page about configuring rEFInd: [URL="https://www.rodsbooks.com/refind/configfile.html"]
https://www.rodsbooks.com/refind/configfile.html[/URL], I did the following:

 I tried putting a second icon inside of the *"myicons"* directory by naming that icon file *"vmlinuz-5-4-0.png"*.

 I also tried naming it with the full name of *"vmlinuz-5.4.0-7642-generic.png"*.

 I also tried naming it *"os_linux.png"* to see if it would perhaps replace the "tux" icon of that name that's in the *"icons"* directory.

 I did this making sure that the *"scan_all_linux_kernels"* option in the refind.conf file is set to (its default) "true".


 In my rEFInd menu, the "Boot" line of text under the 2 OS icons reads, respectively:

 *"Boot EFI\ubuntu\grubx64.efi from NVME0_ESP"*

 and:

 *"Boot EFI\ubuntu\grubx64.efi from SSD_ESP"*

as I named (using GParted) the ESP file-system labels, respectively, *"NVME0_ESP"* and *"SSD_ESP"* to help distinguish between the two OS's.

 However, I still get two instances of just the one icon for both OS's -- the *"os_ubuntu.png"* green MATE icon.

 (The 2nd icon I'm trying to use is similar to that one, but has the letters "MATE" as part of the icon.)

 As far as I can tell, according to the instructions under "Setting OS Icons", this should work.

 Secure Boot is not active.


 *My Question is:*  [I][B]What do I need to do to show two different icons in the rEFInd menu for two Ubuntu-MATE OS's that have the same name and same version number?


[/B][/I](P.S.: Before anyone tells me to put this question on [the rEFInd forum]("https://sourceforge.net/p/refind/discussion/general/"), I've already done that.)

--------------------------------------[B][I]

SOLVED:[/I][/B]   [B]I was close with number (3) above. 

 I just needed to create a folder called *linux* 

-- and then put a bootloader file in that folder 
(I copied the *grubx64.efi* bootloader file from the *ubuntu* dir) -- 

to be able to put an *os_linux.png* file in the /boot/efi/EFI/refind/myicons folder, and have that image file show in the rEFInd menu.[/B]  

-------------------------------------

---

