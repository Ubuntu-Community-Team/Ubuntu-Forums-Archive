---
title: "Perl vs Python ---- Where should I spend my time?"
date: 2009-02-03
forum: General Help
---

### Post by mrhobbeys on 2009-02-03
Hi I am hoping that someone with experience can tell me which is better to devote my time to; perl or python. (ANY advice welcome)And if there is a better place to post this please let me know.

Currently;     *
1. I only have a need to automate tasks such as file copy/send,  compare files and auto update, backup files, search inside of files.

2. I need to be able to do this both on Ubuntu and Windows. 

3. I would really like to have an auto database in which values are filled in based on file changes.

4. I know very little perl, and I am always wanting to learn something more or new.

In the near future;
I need more advanced automation such as; 
1. Auto changes and file creation from formerly mentioned databases.

2. GUI interaction allowing me to enter values and get data and file creation based on database.

3. Advanced Data interaction.

__More Details (if you are interested)__

Current;
1. Files are made on a Simulation CNC program and are then sent to the CNC where they are edited, changed, and created/re-created (I end up with many clutter files). I need to backup the originals and the changed files, but I need the Newest file to always remain in a shared folder. It is also needed to look inside of the files for a term/keyword and then list the files containing.

2. I prefer Ubuntu/Linux to Windows but we have Windows at work and the CNC software does not work in Ubuntu (even with wine) but I still can and do work with the actual program files on Ubuntu when at home.

3. Each file contains values that are entered as an original, then are edited. I would like to have a database that automatically searches the files for these values notates them then looks for changes and notates the new value, while keeping the old as a reference. I would also like to add an easy input that allows me to put in more information not found in the files.

4. Self explanatory.

In the near Future;
1. After enough data has been collected I would like to set things up so that values that need/should be changed are done so automatically (with confirmation). 

2. I would like to set up a GUI that allows me to input extra data, see data in new ways, and add external non-data type information such as pictures.

3. I would like to be able to easily change the way I am looking at the data to possibly find new relations.


I hope this is not too long, I just would like to make sure anyone answering understands what I would like to do. Also I would be very pleased for ANY advice pertaining to what I would like to do.

---

### Post by bruce2000 on 2009-02-03
> **mrhobbeys said:**
> And if there is a better place to post this please let me know.


Hi,

You will probably get a better response in the "Programming Talk" forum:

[http://ubuntuforums.org/forumdisplay.php?f=39]("http://ubuntuforums.org/forumdisplay.php?f=39")

They are rather keen on Python in there.

HTH

---

### Post by Slim Odds on 2009-02-03
Ruby

---

### Post by Simian Man on 2009-02-03
Both are capable of roughly the same things, however I recommend Python for two reasons:

[LIST=1]
[*]Python code is easier to learn to read
[*]Perl is slowly languishing while Python is flourishing
[/LIST]

Good luck!

---

### Post by mb_webguy on 2009-02-03
In general, programming languages can all do the same things, but some do some things better (or easier, or faster) than others.

Perl is an older language, and gradually decreasing in popularity (though still highly ranked among the most popular scripting languages).  It's also not the easiest language to learn.  On the other hand, it's very good at text manipulation, and code written in Perl is generally very compact (if nigh indecipherable).  It also generally executes slightly faster than some other scripting languages.

Python is a fairly easy language to learn, though people with programming experience in C-derived languages may find it a bit weird at first.  Python code is quite a bit wordier than Perl, but also therefore easier to read than Perl.  While Perl is gradually declining in popularity, Python is definitely on the rise, and some sources list it in the top three most popular scripting languages.

Between the two, I'd go with Python, especially if you're relatively new to programming.  I've used a lot of different languages over the years, and I found Perl to be difficult to learn and difficult to read, even after you've used it for a while.  I don't particularly like Python, simply because it's quite a bit different from what I'm used to.  However, it is easy to learn and to read, and it can do pretty much everything you could ask of it.

---

