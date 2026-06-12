---
title: "Nautilus Secure Wipe"
date: 2007-09-11
forum: Desktop Effects &amp; Customization
---

### Post by American_Outcast on 2007-09-11
This is not working well. I am trying to get nautilus to shred files when I right click them, like it use to, but I forgot the command, lol. I have nautilus-actions installed. For now I want to have it shred 50 times and the final pass in zeros.

This is what I have now, it is not working and it doesn't look right to me.

path - /usr/bin/find
parameters - %M -type f -exec shred -ufz50 '{}' \;

Anyone know the problem?

---

### Post by American_Outcast on 2007-09-12
7 hour bump

---

### Post by American_Outcast on 2007-09-12
16 hour bump

---

### Post by robert_pectol on 2007-09-12
Give this script a try:

[http://rob.pectol.com/myscripts/secure-file-delete.sh.txt](http://rob.pectol.com/myscripts/secure-file-delete.sh.txt)

Simply download it to your ~/.gnome2/nautilus-scripts/ directory, change the name to something like, "secure-delete" and make sure it's executable (chmod 755 secure-delete).  Then you can right-click a file or directory and choose, "secure-delete" from the pop-up menu to securely delete it!  You can open the script in a text editor to alter the number of passes under the, "user configurable options" near the top.  The default is 10 passes.  For quicker file deletion, but less secure, decrease the number of passes.  Alternatively, increase the number for more security.  It probably shouldn't be set to anything less than, '2' for any kind of decent secure deletion.  Enjoy!  :-)

---

### Post by American_Outcast on 2007-09-12
Thank you. It looks straight forward enough and very easy to set up.

---

### Post by SpikeyMike on 2007-10-08
> **robert_pectol said:**
> Give this script a try:

[http://rob.pectol.com/myscripts/secure-file-delete.sh.txt](http://rob.pectol.com/myscripts/secure-file-delete.sh.txt)

Simply download it to your ~/.gnome2/nautilus-scripts/ directory, change the name to something like, "secure-delete" and make sure it's executable (chmod 755 secure-delete).  Then you can right-click a file or directory and choose, "secure-delete" from the pop-up menu to securely delete it!  You can open the script in a text editor to alter the number of passes under the, "user configurable options" near the top.  The default is 10 passes.  For quicker file deletion, but less secure, decrease the number of passes.  Alternatively, increase the number for more security.  It probably shouldn't be set to anything less than, '2' for any kind of decent secure deletion.  Enjoy!  :-)

Hi, I also would like to use this, I tried to follow your instructions but I cannot get it to work, I copied the contents of the link into a new file, named it secure-delete and put it in the directory ou said but I don't see it in the pop up menu when I right click on a file. I tried adding an extra entry to the Nautilus Actions Configuration but it still doesn't appear :confused: any advice?

Spikey

---

### Post by robert_pectol on 2007-10-10
It works.  I promise!  Just follow the directions.  Many people are using this script successfully.

---

### Post by DapperMe17 on 2008-07-17
Robert, 

Thanks for a great script!

:guitar:

---

### Post by DapperMe17 on 2008-07-19
Robert,

Do your scripts work in Thunar? 

MintXFCE had a .gnome2 file but of course, there is no nautilux-scripts file.

Could I make a new folder "thunar-scripts" & continue with your script?



Thanks for any input!

---

### Post by tact on 2008-07-19
> **American_Outcast said:**
> This is not working well. I am trying to get nautilus to shred files when I right click them, like it use to, but I forgot the command, lol. I have nautilus-actions installed. For now I want to have it shred 50 times and the final pass in zeros.

This is what I have now, it is not working and it doesn't look right to me.

path - /usr/bin/find
parameters - %M -type f -exec shred -ufz50 '{}' \;

Anyone know the problem?


Forget scripts..  you have nautilus-actions installed...  "sudo apt-get install wipe" and configure in nautilus-actions as per the attached screenshot...

---

### Post by tact on 2008-07-19
...you know of course that if you are using a journalling file system, or any applications that (and they all generally do) create hidden temporary files and strew them around your hard drive, that doing a supposedly secure wipe on a file by itself does not get rid of all the copies, temp files, and the bits of it a journalling file system caches here ant there.

Right?  ;)

---

### Post by DapperMe17 on 2008-07-21
Both of Robert's scripts "do" work in Thunar. :popcorn:

Simply copy to script to a new text document in your home folder. Then, from Thunar, set up "custom actions" and simply point to the scripts. Don't forget to "chmod" each in a terminal window.

The only hitch is in Robert's "encryt/decrypt" script. Everything works great, except, after entering th GPG passphrase to decrypt the file, the original file never re-appears. The GPG'd (encrypted) file still remains, even though the pop-up box says that the file was decrypted ok.


Robert, do you know what the hitch could be? 


Thanks for two "great" scripts!!

---

