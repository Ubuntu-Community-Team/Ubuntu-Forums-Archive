---
title: "Trying to uise alien to convert an RPM file to deb"
date: 2009-05-29
forum: General Help
---

### Post by radi0j0hn on 2009-05-29
In all the how-to's I read, they assume you know where to place the RPM file so alien can find it.

I need a STEP-by-STEP how to that tells me where to put the RPM file and how to specify it in the command.

I've added the alien package

I know to go to a command line, log in as root (sudo bash)

Then I see I should type

sudo alien -k name-of-rpm-file.rpm

I type that, using the name of the rpm package.  In this case VM.rpm

But if my RPM file is on my desktop (as it is in htis case), the file can't be found.

What important bit of instruction is missing?  Is there some assumption that the RPM file is in a certain location, and what would that be?

 TIA  John

---

### Post by TeoBigusGeekus on 2009-05-29
```
sudo alien -k /home/your_username/Desktop/name-of-rpm-file.rpm
```

---

### Post by radi0j0hn on 2009-05-29
Thanks for the specifics!  This now works, but I have more to deal with:

Warning: Skipping conversion of scripts in package VMware-Workstation: postinst prerm
Warning: Use the --scripts parameter to include the scripts.


As usual, it says add "-c" to do this, but not WHERE in the command to place it or if it REPLACES the "-k"

Gotto do more research!  This is about as bad as old DOS commands..and I wrote a book on those!   ;)


Thanks for the good start, though.

---

