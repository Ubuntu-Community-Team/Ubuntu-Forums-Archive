---
title: "***RE-POSTED***.Dell A940 Printer installation - Dell, Tiny, Or Primax?"
date: 2009-07-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by CharmingNathan on 2009-07-26
Dear All,

You will see from my other postings what Zill has helped me do, basically install a compatible Driver for a Dell A940 Multifunctional. I am using Ubuntu - "The Jaunty Jackalope" 9.04

After a week of trying - I am a Newbie - last nght, with the help of the "Installing Lexmark Z55" instructions, I think I succeded in getting the Driver installed, I can certainly send a job to the Printer, but it errors with the diagnostics provided in my earlier post.

However, I think the issue of why the Driver won't print is that Ubuntu is still installing the Dell A940 driver in the device U.R.L. as mentioned earlier - even after un-installing the Dell A940 and physically having the Lexmark Z55 listed, the device U.R.L. remains the same. I have also tried an alternative U.S.B. Port, but with no joy. Any ideas?

The other factor which concerns me, is that primarly whilst I would like to get the Printer Driver installed and working properly from a satisfactory completion point of view, my main requirement for the machine is its Scanner.

Zill checked out information on it, from the Lexmark Website presumably, and expressed doubt as to whether the Driver would act as communication with the Scanner, or whether it was 'just' a Printer Driver.

Can anyone help?

Thanking you in advance.

Nathan.

---

### Post by Liolikas on 2009-07-26
Thy to deal with CUPS:
[http://www.howtoforge.com/ipp_based_print_server_cups](http://www.howtoforge.com/ipp_based_print_server_cups)
You have cups at all?
You see your printer there? you can try test page? Etc.

---

### Post by CharmingNathan on 2009-07-26
> **Liolikas said:**
> Thy to deal with CUPS:
[http://www.howtoforge.com/ipp_based_print_server_cups](http://www.howtoforge.com/ipp_based_print_server_cups)
You have cups at all?
You see your printer there? you can try test page? Etc.

I think C.U.P.S. is installed yes, Liolikas.

When I plug in the Dell A940 Ubuntu does install a Driver for it, but the incorrect one, so I am guessing that is C.U.P.S.?

Thanks for the link, but I didn't really understand most of that which was on the page!

---

### Post by Liolikas on 2009-07-26
ahh...
Try enter this page:
[http://localhost:631](http://localhost:631)
You should see your printer settings there.

---

### Post by CharmingNathan on 2009-07-26
> **Liolikas said:**
> ahh...
Try enter this page:
[http://localhost:631](http://localhost:631)
You should see your printer settings there.

Yes, but it has gone back to installing the Dell Driver, i.e. the incorrect 'original".

This is what it says after sending a print job through....

"/usr/lib/cups/filter/rastertoz55 failed"

**Description:** Dell  A940
**Location:** nathan-desktop
**Printer Driver:** Lexmark Z55 v1.0-1
**Printer State:** idle, accepting jobs,  published. 
**Device URI:** usb://Dell%20/A940 ** ***IIT STATES THIS EVEN WITH THE LEXMARK Z55 DRIVERS INSTALLED?*****

---

### Post by Liolikas on 2009-07-26
Be sure you have THE LATEST drivers...
ah I found this one:
[http://onlyubuntu.blogspot.com/2008/05/howto-setup-lexmark-z55-printer-in.html](http://onlyubuntu.blogspot.com/2008/05/howto-setup-lexmark-z55-printer-in.html)

Dell A940 is Lexmark z55 they are same.

---

### Post by CharmingNathan on 2009-07-26
> **Liolikas said:**
> Be sure you have THE LATEST drivers...
ah I found this one:
[http://onlyubuntu.blogspot.com/2008/05/howto-setup-lexmark-z55-printer-in.html](http://onlyubuntu.blogspot.com/2008/05/howto-setup-lexmark-z55-printer-in.html)

Dell A940 is Lexmark z55 they are same.

Liolikas,

It looks like you didn't check out my previous Posting, I think it's now on page 2!

Attempted and in the end succeeded in installing this Driver with Zill's help.

But you will see that I still cannot Print or Scan.

Check out that other post for more details.

Thanks.

Nathan.

---

### Post by Liolikas on 2009-07-26
It looks more like bug then beginner question then.
Fill in bug report here:
[https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

---

### Post by CharmingNathan on 2009-07-26
> **Liolikas said:**
> It looks more like bug then beginner question then.
Fill in bug report here:
[https://launchpad.net/ubuntu/+bugs](https://launchpad.net/ubuntu/+bugs)

Liolikas,

Thanks for your suggestion, but I wouldn't be so audacious as to suggest this is a bug, for these reasons:

1. I am a Newbie, and it could be an error I am making.

2. It is only with Zill's help I have managed to install the Z55 Driver, and who knows what other issues there maybe that I am unaware of.

3. From what I have read and seen, there appears to be a very good chance that there is NO Driver for the Dell A940 that is really compatible with Ubuntu, and if there is, there appears to be doubt whether it would enable the Scanner.After all, it's possible the Driver for the Scanner hasn't even been written for Ubuntu.

If you really think after what I have said above, in my last and previous postings, that I should still submit this as a bug, I will do so.

Nathan.

---

### Post by Sef on 2009-07-26
This is the problem:

[QUOTE]3. From what I have read and seen, there appears to be a very good chance that there is NO Driver for the Dell A940 that is really compatible with Ubuntu, and if there is, there appears to be doubt whether it would enable the Scanner.After all, it's possible the Driver for the Scanner hasn't even been written./QUOTE]

Therefore it is not a bug.   Dell printers are rebranded Lexmark printers, and Lexmark isvery unfriendly to GNU/Linux.   Best option is to get an older computer, a PIII is fine, with XP, and set it up as a print server.

---

### Post by Liolikas on 2009-07-26
Go submit bug. :P
This printer works for many ppl do not mention scanner in bug if you want.
After all no driver is bug too.

Read this one first:
[https://bugs.launchpad.net/ubuntu/+bug/1](https://bugs.launchpad.net/ubuntu/+bug/1)
As example

---

### Post by Sef on 2009-07-26
> Go submit bug. :razz:
This printer works for many ppl do not mention scanner in bug if you want.
After all no driver is bug too.

No it is not a bug.   Therefore, it is a waste of time to report it.   If the op wants, they could contact Lexmark for they have to make the driver for the printer.   I use and recommend HP because they make drivers for GNU/Linux.

---

### Post by Liolikas on 2009-07-26
> **Sef said:**
> No it is not a bug.   Therefore, it is a waste of time to report it.   If the op wants, they could contact Lexmark for they have to make the driver for the printer.   I use and recommend HP because they make drivers for GNU/Linux.
There is driver already and it works on many other Linuxes just not in Ubuntu.
Lexmark will tell nothing or will suggest to use Fedora 11.

---

### Post by CharmingNathan on 2009-07-26
Liolikas and Sef,

Thank you both very much for your responses.

Due to my lack of experience with Linux Ubuntu (Linux full stop, in fact), and from the in-depth help Zill offered, I can only offer my own opinions from Widnose point of view, and hope that we can come to some sort of reasonable conclusion in this matter:

1. The fact that there is NO direct Dell Support for the A940 suggests no Driver has been written at all.

2. The Driver that has been suggested is the Lexmark Z55 which is apparently the 'real' model number.

3. The fact that the Driver took me three days with Zill's help suggests it is a workaround at best, or that could be down to me being a Newbie?

4. While Liolikas makes the point that others use the Z55/A940 with Ubuntu, this could mean nothing from the Scanner Driver point of view. I would argue that only the fax facility is probably less used than the Scanner.

Sef, while I take on-board your comment about using a Linux Ubuntu 'friendly' device, I have been advised that **ALL** three Scanners I have access to: the Tiny (Primax), Xerox, and Dell are not compatible; it doesn't give me a great start with Ubuntu does it?

Nathan.

---

### Post by Liolikas on 2009-07-26
> 
3. The fact that the Driver took me three days with Zill's help suggests it is a workaround at best, or that could be down to me being a Newbie?

Both.
Super bad luck that ALL three Scanners: the Tiny (Primax), Xerox, and Dell are not compatible. When I started Linux in around 2004 more than half scanners where supported already. 
Write other 2 models full name.

---

### Post by CharmingNathan on 2009-07-26
> **Liolikas said:**
> Both.
Super bad luck that ALL three Scanners: the Tiny (Primax), Xerox, and Dell are not compatible. When I started Linux in around 2004 more than half scanners where supported already. 
Write other 2 models full name.

The Tiny is a re-badged Primax FU661E, the Xerox a 2400.

---

### Post by Liolikas on 2009-07-26
Primax FU661E works on Linux:
[http://www.bioticaindia.com/fu661e.html](http://www.bioticaindia.com/fu661e.html)

---

### Post by CharmingNathan on 2009-07-26
Dear All,

I am trying to install the above onto The Jaunty Jackalope, 9.04 and am a *real* Newbie.

I am told that I need the Lexmark Z55 Driver for this device, but after trying to and finally succeeding installing it over three days, it now brings up an error message.

On top of that, what I really need to use is its Scanner.

Is this a lost cause?

Thanks for your help.

Nathan.

---

### Post by CharmingNathan on 2009-07-26
> **Liolikas said:**
> Primax FU661E works on Linux:
[http://www.bioticaindia.com/fu661e.html](http://www.bioticaindia.com/fu661e.html)

Liolikas,

Someone suggested that this wasn't on the S.A.N.E. list, whatever that is?

The Scanner is in my Workshop, so I wouldn't be able to try it until tomorrow anyway.

I suppose I would like someone to tell me that the Dell A940 is either **definitely** compatible *or *incompatible with Ubuntu, and more specifically the Scanner.

Is that asking too much?! :wink:

Nathan.

---

### Post by Zill on 2009-07-26
> **CharmingNathan said:**
> Someone suggested that this wasn't on the S.A.N.E. list, whatever that is?...
Google is your friend ;-)

[http://www.sane-project.org/]("http://www.sane-project.org/")

[http://www.sane-project.org/sane-mfgs.html]("http://www.sane-project.org/sane-mfgs.html")

---

### Post by Sef on 2009-07-27
> Sef, while I take on-board your comment about using a Linux Ubuntu 'friendly' device, I have been advised that **ALL** three Scanners I have access to: the Tiny (Primax), Xerox, and Dell are not compatible; it doesn't give me a great start with Ubuntu does it?


You had a great start.   You installed Ubuntu, asked for help, and tried to resolve the problem of your printer/scanner.  The problem is a Lexmark issue because they do not build drivers for GNU/Linux.

---

