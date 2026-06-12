---
title: "Looking for Outlook-compatible mail client"
date: 2011-01-16
forum: Desktop Environments
---

### Post by Grenache on 2011-01-16
Hello

I use Windows XP with Outlook 2003 (soon to be Outlook 2010) on my work laptop, and also the same on my home PC.  I copy the .PST file containing my home emails between the two so I still have access to my home emails on my work laptop when I'm away on business.

So, why am I mentioning this on a non-Windows forum?

Well, I'm migrating my home PC to Ubuntu, but I still want to be able to move the mail PST file to & from the work laptop, but I don't know of any Ubuntu mail clients that will work directly on the PST file.  Those that I have looked at will import from the PST file but maintain emails in their own file format, which means I can't read the new ones again using Outlook if I have updated the mail folders with the mail client on Ubuntu.

So, does anyone know of and can recommend any mail clients that work with PST files directly?  The analogy is like using Open office to read & write MS Word .doc & Excel .xls files directly without any importing or exporting.

I should also mention that I've tried unsuccessfully to install Outlook using Wine, but it's not happening, same problems as described in the Wine appdb test results.

Thanks!

---

### Post by skewty on 2011-01-16
It doesn't exist and likely never will.  The .PST file format is terrible.

The closest Linux has is [COLOR="Blue"]_[Evolution]("http://projects.gnome.org/evolution/")_[/COLOR].

Outlook and WINE don't quite work well together as your own results have shown you.  I believe you will have much better luck running Outlook with [COLOR="blue"]_[CrossOver]("http://www.codeweavers.com/products/cxlinux/")_[/COLOR]

If you aren't working with a MS Exchange server, I would recommend switching to another client.

Scott

---

### Post by vidtek on 2011-01-17
> **Grenache said:**
> Hello

I use Windows XP with Outlook 2003 (soon to be Outlook 2010) on my work laptop, and also the same on my home PC.  I copy the .PST file containing my home emails between the two so I still have access to my home emails on my work laptop when I'm away on business.

So, why am I mentioning this on a non-Windows forum?

Well, I'm migrating my home PC to Ubuntu, but I still want to be able to move the mail PST file to & from the work laptop, but I don't know of any Ubuntu mail clients that will work directly on the PST file.  Those that I have looked at will import from the PST file but maintain emails in their own file format, which means I can't read the new ones again using Outlook if I have updated the mail folders with the mail client on Ubuntu.

So, does anyone know of and can recommend any mail clients that work with PST files directly?  The analogy is like using Open office to read & write MS Word .doc & Excel .xls files directly without any importing or exporting.

I should also mention that I've tried unsuccessfully to install Outlook using Wine, but it's not happening, same problems as described in the Wine appdb test results.

Thanks!

Like Skewty said, Outlook is terrible I've been using it for years and lost lots of .pst data files in that time.
  
_*If you don't have an exchange server,*_ you could try Thunderbird, there is a windows as well as Linux version.
 
It's not as good as evolution which has much more of an Outlook feel, but it works well in both o.s's, I have tried it in both.

Best regards, Tony.

---

### Post by kellemes on 2011-01-17
Assuming you always have an internet-connection available you could use Gmail as an email-client, I'm doing this for some time now and have no need for desktopclients.
Just an idea.

---

### Post by Grenache on 2011-01-20
Thanks for all the responses.

The main reason for the OP is that I am often away from home on business, and some of that time not online (e.g. on a plane), and I have a Win laptop which I can't install other apps on.

But copying the PST file containing my personal emails between my laptop and my home PC is working well as a solution for now, but I'm planning to use Ubuntu at home permanently, and this is probably the last obstacle.

Looks like I'm stuck.

Is anyone planning to write a PST-compatible mail client?  I know it's a proprietary format, but Open Office manages the relevant doc and xls files, so can the same be done for psts?

---

### Post by Grenache on 2011-01-20
Thanks for all the responses.

The main reason for the OP is that I am often away from home on business, and some of that time not online (e.g. on a plane), and I have a Win laptop which I can't install other apps on.

But copying the PST file containing my personal emails between my laptop and my home PC is working well as a solution for now, but I'm planning to use Ubuntu at home permanently, and this is probably the last obstacle.

Looks like I'm stuck.

Is anyone planning to write a PST-compatible mail client?  I know it's a proprietary format, but Open Office manages the relevant doc and xls files, so can the same be done for psts?

---

### Post by Grenache on 2011-01-20
Apologies for the multiple posts, not sure what happened.

---

### Post by nomko on 2011-01-20
> **Grenache said:**
> Thanks for all the responses.
 
The main reason for the OP is that I am often away from home on business, and some of that time not online (e.g. on a plane), and I have a Win laptop which I can't install other apps on.
 
But copying the PST file containing my personal emails between my laptop and my home PC is working well as a solution for now, but I'm planning to use Ubuntu at home permanently, and this is probably the last obstacle.
 
Looks like I'm stuck.
 
Is anyone planning to write a PST-compatible mail client? I know it's a proprietary format, but Open Office manages the relevant doc and xls files, so can the same be done for psts?
 
There's a solution to convert your .pst file in such a way that the mails can be  imported in Evolution. The solution is called **readpst**.
Here you ca find more info: [http://ubuntuforums.org/showthread.php?t=39627](http://ubuntuforums.org/showthread.php?t=39627).
And also here is more info: [http://www.five-ten-sg.com/libpst/rn01re01.html](http://www.five-ten-sg.com/libpst/rn01re01.html)

---

### Post by vidtek on 2011-01-21
> **Grenache said:**
> Thanks for all the responses.

The main reason for the OP is that I am often away from home on business, and some of that time not online (e.g. on a plane), and I have a Win laptop which I can't install other apps on.

But copying the PST file containing my personal emails between my laptop and my home PC is working well as a solution for now, but I'm planning to use Ubuntu at home permanently, and this is probably the last obstacle.

Looks like I'm stuck.

Is anyone planning to write a PST-compatible mail client?  I know it's a proprietary format, but Open Office manages the relevant doc and xls files, so can the same be done for psts?

If Nomco's solution doesn't work, you can always import the .pst file into Thunderbird in windows,
then export to evolution from linux Thunderbird.  

That's what I did with my data and contacts from my .pst file.

Tony

---

### Post by Grenache on 2011-01-25
Thanks vidtek and nomko, but that doesn't help me once I want to resume working with my mail on outlook again, as I need to be able to work on my mails (send/receive/delete/etc) on my home PC ubuntu), then transfer the files back again to the laptop and continue to work on the same emails using outlook on XP.

What seems to be the problem is that there doesn't seem to be a reliable way to create a new pst file on unbuntu which I can copy to the laptop to use with outlook.

Thanks anyway.

---

### Post by nomko on 2011-01-25
> **Grenache said:**
> Thanks vidtek and nomko, but that doesn't help me once I want to resume working with my mail on outlook again, as I need to be able to work on my mails (send/receive/delete/etc) on my home PC ubuntu), then transfer the files back again to the laptop and continue to work on the same emails using outlook on XP.
 
What seems to be the problem is that there doesn't seem to be a reliable way to create a new pst file on unbuntu which I can copy to the laptop to use with outlook.
 
Thanks anyway.
 
What about using Outlokk under Wine?
Or even install Windows under VirtualBox?
Might that be a solution?

---

### Post by vidtek on 2011-01-25
> **Grenache said:**
> Thanks vidtek and nomko, but that doesn't help me once I want to resume working with my mail on outlook again, as I need to be able to work on my mails (send/receive/delete/etc) on my home PC ubuntu), then transfer the files back again to the laptop and continue to work on the same emails using outlook on XP.

What seems to be the problem is that there doesn't seem to be a reliable way to create a new pst file on unbuntu which I can copy to the laptop to use with outlook.

Thanks anyway.

You are right, there is no way to do what you want reliably and easily. Perhaps you need to re-think what you actually wish to achieve.  Google mail is probably the most reliable and easiest way to get to where you want to go, which means ditching Outlook altogether, and using google mail and associated utilities.
Are you using a feature in Outlook you simply can't leave behind that is not catered for in a 3rd part app you can use in conjunction with Google?
Best regards, Tony.

---

### Post by RikoW on 2011-01-26
Hi,


with your current approach of moving .pst files back and forth, I believe you are stuck with Outlook. I recommend purchasing a copy of Crossover Office from [Codeweavers]("http://www.codeweavers.com/") which gives you the possibilities to run Outlook currently up to version 2007.

I run MS Office 2007 (and 2003 before) especially for Outlook since some years now under Crossover and I'm extremely happy with it. Evolution never really worked for me. Means however, you need to invest 37 Euro for the Standard Edition (or 64 Euro for Pro). They have trial version you can download and test.

Cheers,
         Riko

---

