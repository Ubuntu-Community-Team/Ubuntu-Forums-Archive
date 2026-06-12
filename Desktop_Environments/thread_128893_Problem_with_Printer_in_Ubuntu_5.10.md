---
title: "Problem with Printer in Ubuntu 5.10"
date: 2006-02-12
forum: Desktop Environments
---

### Post by pito on 2006-02-12
Hello...

I do use Xerox M750 printer with Ubuntu 5.10 with connection to
parallel port. 

In System-Administration-Printing i add the new printer M750 from the list of printers. All fine so far.

When starting to use it, the files are send to printer but nothing happend.

Any idea what to do ?

How to verify the setup ?

The printer worked perfect in Fedora C3

Will apreciate for help.
/piotr

---

### Post by pito on 2006-02-12
It is me again.

I just tested another printer, this time HP PCS-2355 with USB connection
and it works perfect.
Any idea ?

/PiTo

---

### Post by moontide on 2006-02-13
I've got major printer problems too. Epson Stylus photo 915, Ubuntu 5.10.

I have managed to get it run on two occassions after lots of tweeking but both times it works once and then gives the printer paused message and wont print again. 

I think I sucessfully installed the gutenprint 5.0.0rc2. Also, I set myself up to administer via the cups website, but still no go. 

This printer has worked beautifully on lots of other linux distros. I'm really stuck this time.

Any suggestions welcome. I seem to have exhausted google search options.

Just like to add: I just installed turboprint and experienced the same thing, It printed fine the first time and from then on wouldn't print again. Just reports "turbo paused"

Is there some way I can track down whats wrong?

---

### Post by pito on 2006-02-13
Thanks for info...
What I would like to do is to connect som kind of debuger or network analyzer.
At my previouze job I had access to that kind of stuff.
But not now.

My plan would be.
1. Run on Fedora ( it is working there) and make a log how the Driver talks to the Printer
2. Run it agn on Ubuntu and verify what happends there.

I have fixed that kind of problem with a USB device that worked on Mac but crashed on Windows. Of couse the Windows did not followed the device protocol.

If any one have possibility, time it would be interesting.

But as I mentioned earlier the USB HP PSC2350 works fine. My suspession is problem with either parport or with the driver itself.

/PiTo

---

