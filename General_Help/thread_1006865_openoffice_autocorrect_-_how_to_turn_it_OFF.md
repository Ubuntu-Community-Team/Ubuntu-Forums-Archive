---
title: "openoffice autocorrect - how to turn it OFF ??"
date: 2008-12-09
forum: General Help
---

### Post by johnlvs2run on 2008-12-09
The autocorrect has to be the MOST annoying feature ever invented on computer.

This is what I would like to do. 
1)  Have the decimal numbers as I put them in and not change them.
2 = 2 ........................ not 2.0000
5.629 = 5.629 .......... not 5.63 ... not 5.6290
- 6.4 = - 6.4 .............. not -6.4
nov08 = nov08 ......... not 11/08/2008 

Can anyone help me to turn off the autocorrect?  Thanks.

---

### Post by Iowan on 2008-12-09
I have OpenOffice 2.3.0. I found this:> By default, OpenOffice.org automatically corrects many common typing errors and applies formatting while you type. 
To quickly undo an automatic correction or completion, press Ctrl+Z. 
[COLOR="RoyalBlue"]To turn off most AutoFormat features, remove the check mark from the menu Format - AutoFormat - While Typing.[/COLOR]

---

### Post by johnlvs2run on 2008-12-09
Thanks for your reply.

Control-Z is reinforcing the autocorrection.

Under format > autoformat > there is no option "while typing" to uncheck.

---

### Post by frankleeee on 2008-12-09
> **johnlvs2run said:**
> Thanks for your reply.

Control-Z is reinforcing the autocorrection.

Under format > autoformat > there is no option "while typing" to uncheck.

Look in the help part of OO there are more ways to approach the problem, and the ctrl+z command is only part of the answer using that command.

---

### Post by johnlvs2run on 2008-12-09
I've been doing all as instructed in help and the menu for hours, way too long.
It should not be this difficult to have it stop changing my typing.


In lieu of this, could someone recommend an easier to use program for word processing and spreadsheets?


Thanks.

---

### Post by beansdad on 2009-03-05
I hated the autocorrect feature in the costly alternative system along with lots of blue screens etc etc so was very pleased to start using Linux and Ubuntu which gave very few problems.
I've just started using spreadsheets seriously and find that, although autocorrect can be turned off for most things, a date type text entry will be converted unless you use an apostrophe in front of it.
Why on earth do programmers think they know what people want and include things which cannot be sensible options.
I would dearly like computer programs to work for me not do what programmers have decided I want!!
If any programmers/developers do read this - PLEASE, PLEASE make any corrections OPTIONAL not automatic!!

---

### Post by beansdad on 2009-03-05
In spreadsheets the autocorrect function is turned off in Tools>Cell Contents and then uncheck the Autoinput option.

Alas, this doesn't stop date conversion!!

It may cure the numbering problem but you may have to use the Format>Cell>Numbering option.:(

---

### Post by dalrympm on 2009-05-15
I just whacked my head against the wall about this for a little while and figured out what was affecting me.  I guess the "feature" we're trying to overcome is the format recognition being used in tables in the word processor.  When I put in 2.2.11, it so helpfully assumed I wanted 02/02/11.  This doesn't seem to have anything to do with autocorrect.  I finally got it fixed by:

- right click on cell with the problematic data
- select "Number Format..."
- select "Text" in the Category column
- re-enter your data in the cell
- voila (I hope)

WAY ANNOYING

---

### Post by hamptone on 2009-11-06
It's sad that I have to throw away an entire program mearly because there is no way to enter in dates as text (i.e. August 22 2009).  Such a tiny problem that could be fixed with a check box makes OpenOffice unusable for me and I'm forced to result to... MS. sigh. I try to support open source and every so often make the switch, but it there is always something that pushes me back.

---

### Post by raindog469 on 2009-11-07
Just discovered that in Openoffice 3.1.1 Writer, the way to prevent it from forcing "November 2009" to "11/01/09" (even though AutoCorrect and AutoFormat are disabled) is to select the whole table cell in which you're entering the text, open Table/Number Format, and set the format to Text ("@").  For some reason, just putting the cursor in the cell is not enough.  

I assume this is a bug caused by sloppy integration of Calc's cell formatting into Writer's table support.

---

### Post by Hagar Delest on 2009-11-07
For Writer, see [[Solved] Problems Auto Formatting a Table in Writer](http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&t=22145).

---

### Post by aspergerian on 2010-03-27
I too have to fight against various Autoformat impositions mandated by OpenOffice and wish there were one easily findable switch for disabling ALL - as in really, truly ALL - autoformat options. Having to try to disable N1, N2,... Nn features is frustrating and a waste of time - and often leaves various Autoformat offenders still wreaking their havoc.

---

### Post by MichaelSnow on 2013-03-28
> **dalrympm said:**
> I just whacked my head against the wall about this for a little while and figured out what was affecting me.  I guess the "feature" we're trying to overcome is the format recognition being used in tables in the word processor.  When I put in 2.2.11, it so helpfully assumed I wanted 02/02/11.  This doesn't seem to have anything to do with autocorrect.  I finally got it fixed by:

- right click on cell with the problematic data
- select "Number Format..."
- select "Text" in the Category column
- re-enter your data in the cell
- voila (I hope)

WAY ANNOYING

Way, way, WAAAAAAAY annoying... at least there IS a way to disable this "feature", but I'd have had much better use of my time, if this program was set by default to take me literally.
In any case thank you for the effort you spent discovering and posting this. You might have prevented an aneurysm, today :)
Maybe in future versions of the software, implementation of voice recognition/activation would be in order... For example, this past 30 minutes could have been better spent if I could simply have verbally instructed OO with a phrase such as:
   "Yes, OpenOffice... I'm sorry, I know 1.12.1 isn't a logical number, but trust me on this."
to which it could respond with:
   "Oh. Okay. [beep-bloop-bleep-boop] Reverting '01/12/01' back to '1.12.1'... sorry for the inconvenience".

---

### Post by oldos2er on 2013-03-28
Old thread closed.

---

