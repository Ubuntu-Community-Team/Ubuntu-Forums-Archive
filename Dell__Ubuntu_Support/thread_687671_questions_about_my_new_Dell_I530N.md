---
title: "questions about my new Dell I530N"
date: 2008-02-04
forum: Dell  Ubuntu Support
---

### Post by BertP on 2008-02-04
Well my old pc, circa  2003 (which was no powerhorse even then)  died,  so I called Dell to asked about their low-cost Ubuntu solutions and  their rep recommended the Dell Inspiron Desktop 530 N.


I went ahead and said yes without asking too many question so I hope you guys will indulge me...  It arrived just a while ago and It's lightning fast compared to the old machine! :)
  
1) The processor is an Intel® Pentium®  dual-core processor E2140 (1MB L2,1.60GHz,800 FSB).  A feature chart  I found on the web somewhere said this is a 64 bit processor;  if so, is the version of Ubuntu 64 or 32 bit?


How is it partitioned?  when I go to Places->Computer, Other than the DVD,  I see volumes labeled "Dell Utility", "OS" & "Filesystem".
"Dell Utility" wants the supervisor's password to access.
"OS"  gives me a "Cannot Mount Volume'
and "Filesystem" lets me navigate through Ubuntu's file system without asking for a password
What is the purpose for these volumns?.

Also what format is the partiton(s)?  I am guessing it is not NTFS but is it formated usiong the format  that is compatible with Windows' Fat32?  (I am a noob and don't remember thier names)


The automatic spellchecker in FireFox is driving me crazy!. I think it is configured like my old computer; "Check Spelling As I Type" is checked in the Firefox preferences with the language being United States English BUT EVERY WORD  is initially flagged as misspelled. Sometimes when I hit the "enter key" the red underlines on every word will disapper from the paragraph but just as often every word remains marked as misspelled..  what am I doing wrong?
  

The graphic effects are very cool.  My other computer was never powerfull enough to use them. A few minutes  ago I was stuck with the "Move" cursor, not knowing how to change back into  regular mode.  Could someone direct me to documentation for these features?

Dell's  webpage says the following:
---
In addition to new 3D visual effects, an easy-to-use desktop search engine and pre-installed Flash, we’ve added native DVD playback and improved back up, recovery and restore options.
----

a couple of questions:  Do I need to be concerned about accidently replacing the codecs used for  DVD playback?  Will the DVD codecs be available to other multimedia-type application requesting compatible codecs?.

Is there detailed list which shows the differences between standard  Ubuntu and Dell's configuration?

Thanks guys!  except for the annoying instant speller checker malfunction,  every thing looks great!

---

### Post by gbrainin on 2008-02-05
I'll answer what I can:

The OS is the 32-bit version.  The 64-bit version is still incompatible with a bunch of stuff.  Stick with 32 for now, unless you have some need to switch.

You can see the partition details at [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Default_Partitions]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Default_Partitions").  Basically, there's a small partition with the emergency restore (to factory default), a smaller partition with some utilities, and the linux partitions.  You ordinarily should not need to access them at the partition level.  As you get more advanced, you may want to split your linux partition into subpartitions, but that's a whole other discussion.

The restore and utility partions are some sort of windows type.  The linux partition is usually ext3.

You can find other useful information about Dell's linux on the [Dell linux wiki]("http://linux.dell.com/wiki/index.php/Wiki_Main_Page").

Good luck, and enjoy your new computer!

---

### Post by BertP on 2008-02-05
Thanks for the help!
-----------
I found how to fix my spell check problem!:  No matter how I changed the settings from the menu  "edit->preferences"  the problem persisted but when right clicking on a word marked as misspelled and changing the language selection from this right-click menu fixed the problem.
-----------
The link below lists details on Dell's Ubuntu 7.10 configuration.   Also the video at the bottom shows an I530N in action

[http://direct2dell.com/one2one/archive/2007/12/19/38924.aspx](http://direct2dell.com/one2one/archive/2007/12/19/38924.aspx)

---

