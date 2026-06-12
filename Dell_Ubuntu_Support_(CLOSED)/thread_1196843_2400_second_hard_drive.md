---
title: "2400 second hard drive"
date: 2009-06-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by PartsMan on 2009-06-25
Any tips or warnings on putting a second hard drive in a Dimension 2400?

---

### Post by PartsMan on 2009-07-07
OK
I got a 9.5g Maxtor HD free at work.
It is laying in my extra 5.25 slot.
Going to make mount to keep it there.

I had to unhook my CD to get it to work. Both HD and CD were primary.
Witch should I make secondary?

Also. What type of format should I use? 
There are plenty of choices in partition editor.

---

### Post by ugm6hr on 2009-07-08
I would recommend keeping both HDs as primary devices (i.e. CD secondary), but I'm not certain it actually matters.

Ubuntu uses ext3 as the default format, no reason not to use that.

---

### Post by PartsMan on 2009-07-08
Tried but I would have to get a different cord.
The cord for my main hard drive is just barely long enough and only has one plug.

I went ahead and put it in how I could with what I had.

Primary master - 80g HD (with OS and programs)
Primary slave -  none
Secondary - master 9.5g HD (meant for documents only)
Secondary - slave CD (made it the slave only because it had instructions)

After a little fiddling all are working fine.
Any reason this won't work long term?

---

### Post by ugm6hr on 2009-07-08
> **PartsMan said:**
> Any reason this won't work long term?

No.

In fact, that is what I meant; the words just came out wrong!  I believe HDs are best as master rather than slave.

---

### Post by PartsMan on 2009-07-08
> **ugm6hr said:**
> No.

In fact, that is what I meant; the words just came out wrong!  I believe HDs are best as master rather than slave.

Now that's what I like to here. 
Thought it might be faster that way. Separate drives on separate cables.

I did a little get creative mounting a 3.5" in a 5.25" hole.
Nothing a drill and some L brackets couldn't fix.;)

---

### Post by PartsMan on 2009-07-12
New problem.
I can't save to or create a file on the "new' hard drive.

---

### Post by ugm6hr on 2009-07-12
> **PartsMan said:**
> New problem.
I can't save to or create a file on the "new' hard drive.

Is this a "permissions" issue?

What happens when you try to copy a file to the new HD.  Try using sudo to see if it works.  i.e.

```
gksudo nautilus
```

If this works, you need to change permissions.

---

### Post by PartsMan on 2009-07-12
Ah yes I didn't have permission.

Wow lots of threads on that one here.(searched permission)
Kind of an odd way of doing things.

It is working fine now.
Thank you!

---

### Post by gefurshky on 2009-08-15
Hello, I'm a newbie to Ubuntu, and this is my first post.

This question concerns which (IDE?) cable to use for the second hard drive.  My 2400 has one HD and two CD drives (one is RW).  There are two cables from the board: one goes to the HD and the other goes to the CD drives.  There is only one connector on the cable that goes to the HD.

My idea is to remove one of the CD drives and stick the new HD in that bay.  Will it work to connect it with the connector from the removed CD drive?

Another question: Will a "Type ATA-100 Connector 40 pin IDC" drive work in the 2400?  Like a Seagate UDMA/100 IDE Hard Drive ?

Thanks much!

---

### Post by ugm6hr on 2009-08-16
> **gefurshky said:**
> My idea is to remove one of the CD drives and stick the new HD in that bay.  Will it work to connect it with the connector from the removed CD drive?

Yes.  As long as it is an IDE HD.

Just use the junpers (or cable setting) to make the HD master (rather than slave).

---

### Post by PartsMan on 2009-08-19
I have got another cable for mine now. Currently running 2 hds and 2 cd drives.
If i get a chance I will get a pic of where I have mounted the second drive.

---

