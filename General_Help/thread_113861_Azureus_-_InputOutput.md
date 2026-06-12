---
title: "Azureus - Input/Output"
date: 2006-01-07
forum: General Help
---

### Post by Strukt on 2006-01-07
Hi,

Using ubuntu on a computer wich is my download server, i remote to it through VNC and that works just fine. But azureus doesnt really work. It doesnt matter wich torrent i download and from where but eventually it will come up with this error:

Error: Input/output error, write fails, flush fails when processing file 'a file'

Any ideas on what to about this problem, azureus is the newest version and i am also using SUNs java. 

The harddrive downloading to is a 160GB drive formatted with ext3.

Any ideas for what do do? :) Just reply if you need more in specific information as i am not sure what to include for you guys. Maybe it is a permission problem on the folder? (/dev/hdb1 mounted at /download)

I also want to give a compliment for this operating system, i usually use gentoo but now i wanted a desktoop system up and running as fast as possible and this was really neat, it just works. Well, most of it anyway :)

---

### Post by mad_phoenix on 2006-01-07
Hmmm... ya know I just reinstalled Ubuntu and there's a newer version of Azureus out, and it really doesn't seem to work as well as the last one.

I'm gonna checkout sourceforge.net and see if maybe the older version works better.  As far as getting input/output errors..try setting your download directory for both the .torrent and the files somewhere in your home directory.  That's a good way to find out whether it's a permissions problem or not.

--mad_phoenix

---

### Post by Strukt on 2006-01-07
Good idea, im gonna try that one out.

Let me know what results you get with a older version.

---

### Post by Strukt on 2006-01-07
Well its working if im not downloading to the mounted "folder".

What type of permissions should i have on that folder?

---

### Post by mad_phoenix on 2006-01-07
> Let me know what results you get with a older version.

Well, I downloaded version 2.3.0.4, and it seems to be having the same problems.  Hmmmm....

On my old ubuntu install with working azureus I think I had the sun jre, whereas now I have blackdown.

> What type of permissions should i have on that folder?

Well, it has to be readable and writable to the user.  You could try making the /download directory owned by your user, giving you all permissions (probably safest on a single user system):

```
sudo chown -R <username> /download
```

Give that a try.  I'm gonna investigate my non-starting azureus problem and get back.

--mad_phoenix

---

### Post by Luke771 on 2006-01-07
I KNOW how to fix this, if you can download in your home directory, then the problem *is* about permissions; all you have to do to download to any directory other than home is to run Azureus as "super user" (sudo= super user do, I figured that out! am I smart or what? :-) ). 
You can simply type "sudo azureus" (without the quotes of course) in a terminal window, but then you will be stuck with a terminal windows on screen that you can turn off without shutting down Azureus too; so my solution to taht is:
Add an Azureus launhcher to the panel, then right-click it, choose "properties" and change the command line "azureus %U" to "sudo Azureus U%". That should do the trick, now you can set Azureus to download to *any* directory on *any* partition without gettig any error messages. 
Don't forget to check the  "enable incremental file creation"  checkbox if you have Azureus to write to a FAT32 partition, and absolutely DON'T set it to download to a NTFS partition. (but you knew about that last one already, didn't you).
OK that was it.
Happy downloadings.

---

