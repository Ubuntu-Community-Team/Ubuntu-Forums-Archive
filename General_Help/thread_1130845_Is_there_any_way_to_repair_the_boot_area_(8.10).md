---
title: "Is there any way to repair the boot area (8.10)"
date: 2009-04-20
forum: General Help
---

### Post by De-Apex'd 7 on 2009-04-20
As of yesterday my Ubuntu will no longer boot.  I get a few errors, one of which is 'cannot find /sbin/init'.  Is there any way to use the live CD to repair this issue?  I'd rather not lose all the information by reinstalling Ubuntu if I could avoid it.

---

### Post by meierfra. on 2009-04-20
In order to get a clearer picture of your setup, I suggest from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by De-Apex'd 7 on 2009-04-20
Thanks for the reply, but I think I found my problem.  I run a SeaGate HD and I started thinking it might be the HD.  I ran their diagnostic software and it said my drive failed the test.  I guess I'm going to start looking for a new drive.  If I can get the current HD warrantied I think I will just run the replacement as a slave.  I don't know if I trust SeaGate if it is going to fail in less than a year of use.

---

