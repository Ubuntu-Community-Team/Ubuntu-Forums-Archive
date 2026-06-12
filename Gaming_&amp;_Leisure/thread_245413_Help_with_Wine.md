---
title: "Help with Wine"
date: 2006-08-27
forum: Gaming &amp; Leisure
---

### Post by jadugartir on 2006-08-27
Im trying to get wine working on my new ubuntu installation. If i can get games to run, im going to delete my windows partition and use ubuntu full-time.

But i cant figure out how to get wine to see my "C: drive"

when i type winecfg in terminal, this is exactly what i get:

Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/jeff', starting in the Windows directory.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/', starting in the Windows directory.


any ideas what i can do? My goal is to install and run World of Warcraft ultimately, and im trying to follow the instructions in the threads for this, but this problem is standing in my way.

---

### Post by yfronto on 2006-08-27
When you say 'C Drive', are you refering to your windows partition?

---

### Post by jadugartir on 2006-08-28
no, i mean the fake c: drive and windows directory that wine is supposed to create.

---

### Post by kaptainlange on 2006-08-28
It sounds like it's looking for the fake drive_c in your home directory.

```

Warning: could not find DOS drive for current working directory '/home/jeff', starting in the Windows directory.

```

I believe that it should be looking to '/home/jeff/.wine'.

Not sure why it would not have set that as the working directory originally.

---

### Post by PCalitrack on 2006-08-28
I don't claim to know too much, but I am not sure if you can set your fake C:\\ drive to look for your real Windows drive. Maybe move the files to the location of the fake drive?? 

BTW, the fake drive should be 
> cd ~/.wine/drive_c

---

