---
title: "Texmaker spell checker"
date: 2010-06-03
forum: Education &amp; Science
---

### Post by bauschaw on 2010-06-03
Hi, 
 I just updated to ubuntu 10.04 from 8.04. I was using Texmaker before, but after the update the spell checker stopped working. I am getting the error message "Error: Can't Open Dictionary" when I try to run the spell checker.

 I checked out the texmaker documentation and found this post: [http://lists.alioth.debian.org/pipermail/debian-science-maintainers/2008-June/000035.html](http://lists.alioth.debian.org/pipermail/debian-science-maintainers/2008-June/000035.html)

 I followed the directions and went through: Options -> Configure Texmaker -> Editor

 I then set Spelling dictionary to: /usr/share/texmaker/en_US.dic

 The file is there and opens file in a text editor, and the permissions are set so that all users can read it. I re-started Texmaker a few times and the path to the dictionary is retained. But I keep getting the same error, that the dictionary can't be opened.

 Has anyone had this problem before or know what might be causing it?

 Thanks,
 Andy

---

### Post by wdlang on 2010-06-06
i have the same problem

i installed ubuntu last night

i can find the en_GB.dic in the directory!

---

### Post by Manojo on 2010-06-10
If you meant that you cannot find the dictionary, check in /usr/share/myspell/dicts.

Cheers,
manojo

---

### Post by virsto on 2010-06-18
I am running texmaker (1.9.9) on Ununtu 10.04 and overall it works fine (as expected). However, I recently found that the spell checker did not function. 

I download en_GB.zip, extracted en_GB.dic and placed it /usr/share/texmaker (which is suggested by texmaker).

I still am unable to do spell checking. I get the following error message:

Error: Can't open the dictionary.

Any help on fixing this problem would be greatly appreciated.

--Thank you,
V.

---

### Post by kloxpur on 2010-06-18
Hi, 
I really need the dictionary to be working too. I'm starting to write an report and the dictionary is really needed :S. If any one have an solution please help with. 

Ubuntu 10.04
Texmaker 1.9.9


Regards.

---

### Post by fnchooft on 2010-06-18
Hi everyone,

Texmaker works fine under ubuntu 10.04, and there is no need to download dictionaries.
Use apt-get to find packages myspell*:
sudo apt-cache search myspell

For instance to install french dutch and german (my case) just type:
sudo apt-get install myspell-fr myspell-nl myspell-de-de


Then in texmaker configure the correct path in the editor tab:
/usr/share/myspell/dicts/<You will find the dictionary files here>

This should save you a lot of time, and the dictionaries will get updated automatically.

Kind regards,

Fabian

---

### Post by virsto on 2010-06-18
Thanks Fabian! 
This seems to work fine.

--V

---

### Post by nortexoid on 2010-06-19
> **fnchooft said:**
> Hi everyone,

Texmaker works fine under ubuntu 10.04, and there is no need to download dictionaries.
Use apt-get to find packages myspell*:
sudo apt-cache search myspell

For instance to install french dutch and german (my case) just type:
sudo apt-get install myspell-fr myspell-nl myspell-de-de


Then in texmaker configure the correct path in the editor tab:
/usr/share/myspell/dicts/<You will find the dictionary files here>

This should save you a lot of time, and the dictionaries will get updated automatically.

Kind regards,

Fabian

Thanks! This worked for me, but I wonder why you can't download one of the openoffice dictionaries from the site texmaker links to in the configuration dialog. How on Earth is one to know that the myspell dictionaries must be used?

---

### Post by larsonj on 2010-08-31
There is no need to install anything to get spell check working in Texmaker if Openoffice.org is installed.  Just point the spelling dictionary to "/usr/share/hunspell/en_US.dic" under Options > Configure Texmaker > Editor (to use the default dictionary from Openoffice.org for a United States English installation). 

Other localizations can be found in the "/usr/share/hunspell" directory.  Alternatively, you can check under Tools > Language Settings > Writing Aids in OpenOffice.org Writer to see what's being used with your system.  If nothing is installed already, then follow the instructions in previous posts on this thread to install a spell checker.

---

### Post by sergio91pt on 2010-10-28
as larsonj said use the ones in /usr/share/hunspell/
I was looking for the pt-pt dic, and the myspell package installs it to the hunspell directory wich works!

guys, you might want to use [TexMakerX]("http://texmakerx.sourceforge.net/") instead, as it has an option to change to GTK!

---

### Post by Matths87 on 2010-10-29
Thank you, nortexoid, you really saved my life: I was getting insane without the spell checker.

---

### Post by singingsingh on 2012-04-10
> **Manojo said:**
> If you meant that you cannot find the dictionary, check in /usr/share/myspell/dicts.

Cheers,
manojo
thanks man

---

### Post by overdrank on 2012-04-10
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

