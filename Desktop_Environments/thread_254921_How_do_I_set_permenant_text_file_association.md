---
title: "How do I set permenant text file association?"
date: 2006-09-10
forum: Desktop Environments
---

### Post by Gotou on 2006-09-10
Hi! Why do my text (*.txt) files behave differently on each of my Ubuntu computers?

1st Method:
I'll fire up gedit, type something up and save it on one computer.  The icon that appears is a white rectangle with the upper right corner folded over with the file name below the icon.

2nd Method:
On the same computer I'll right click > Create Document > Plain Text File.  This will fire up gedit, type something up, save and now the icon looks like a miniature page from a 3-ring binder.

When I transfer a text file created by using the 2nd method to another Ubuntu computer and double click on it, a screen pops up saying:

Do you want to run "Boiled Water Recipe.txt", or display its contents?  "Boiled Water Recipe.txt" is an executable text file.
<Run in Terminal> <Display> <Cancel> <Run>

I get the same screen whenever I open a text file that was created in Windows Notepad.

I would like the text files to open with gedit by default without the question screen popping up.  Is there a file association process I need to go through to do this?

I've tried right clicking on the text file > Open with Other Application > Text Editor (and even "Use a custom command" - gedit) but that doesn't make a permanent file association.

Any other ideas?

Thanks!

---

### Post by mdurham on 2006-09-10
Take a look at 'properties' on a text file. Select 'Open With' and select Gedit (or whatever).
Now select 'Permissions' and make sure the 'execute' box is not selected.
It will only ask if you want to execute the file if the 'execute' box is selected (ticked)

---

### Post by spvo on 2006-09-10
Yeah I had this issue also.  Are you saving the text files to a fat32 partition by any chance?

Fat can't handle the permissions properly, so anything saved to that automatically gets set with 777 (rwxrwxrwx).  So when you double click it, linux doesn't know whether to run it as a program or open it as a text file.  The text files you create with a linux program and save to a linux partition get the permission 644 (rw-r--r--).  This way linux knows its a text file only.

---

### Post by fragos on 2006-09-10
File associations are by mime type.  Right click any sample of a type and click properties.  There you can select the icon for the type and select an open with type.  This setting holds for this user on this computer.  Selecting a different icon theme will change all icons but not the applications associated with a mime type.  Icon preferences related to preview are selected in Nautilus Preferences for Preview.  Again this is a by user basis.  Confusion my come from the fact that the promary user has two personalities as user and when performing admin functions.

---

### Post by Gotou on 2006-09-15
Thanks for the suggestions everyone!

A couple weekends ago I replaced Windows with Ubuntu on all my computers.  Now I have a mix of Ubuntu and old Windows text files.  These text files are scattered amongst many directories in a seperate partition.  Is there a way to change the file permissions of just the text files all at once?  I've made a lot of notes over the years.

Thanks!

---

### Post by fragos on 2006-09-15
I haven't actually tried this but have used something similar to delete bakup files.  Before running change the working directory to the directory tree with all the text files.  Assuming my coding is correct the next command should change the permissions of all files in the tree of name *.txt to RW for all users.

find -name *.txt|xargs -i chmod 666 {}

---

### Post by bobosity on 2006-09-15
try this:

make sure you're in the top of the right directory tree.

chmod -R 666 *.txt

---

### Post by Gotou on 2006-09-16
Thanks everyone for the suggestions.  I tried a combination of fragos and bobosity's commands and had a teaser but no success yet.

This is what I tried:

locate /mnt/myjunk/*txt | less

This did spew out a list of all the text files in the "myjunk" directory and sub-directories.  Partial success.

Then I tried the same thing with chmod on the end.  That's where it bombed.

locate /mnt/myjunk/*txt | chmod 666

I got an error message saying chmod was missing an operand after 666.

So I tried

locate /mnt/myjunk/*txt | chmod 666 *txt

and got:

chmod: cannot access `*txt': No such file or directory

Grrr!

Turned it on it's end:

chmod -R 666 | locate /mnt/myjunk/*txt

This spewed out a list of all txt files but it didn't change the mode.

I'm going to try a few more combinations.

Does this give anybody some ideas what might work?

Thanks!

---

### Post by stylishpants on 2006-09-16
...

> I'm going to try a few more combinations.

Don't!  You don't know what you are doing.  Running commands you don't understand and trying random combinations of commands can really screw things up.  You could delete or irreversibly corrupt your data.  You could break your system.

Instead, read the man pages (man <command>) to figure out what you are doing before you do it.  And keep asking for help here when you need it, of course.


The command you are looking for is this:

    find /mnt/myjunk -name \*.txt -exec chmod 666 {} \;


Another option (same results) would be this:

    locate /mnt/myjunk/*.txt | while read f; do chmod 666 $f; done

---

### Post by bobosity on 2006-09-18
Well you're right about just trying commands at random. (although I have learned quit a bit by reinstalling my system a few times)  ;-]

The problem I seem to run into is understanding the man pages. Take the chmod command mentioned above. My reading suggested the '-R' option would traverse the directory tree. What does it really do and how would I have figured out to do it the way stylishpants came up with?

8-)

---

### Post by Gotou on 2006-09-20
Thanks for the warning stylishpants.  No worries, though.  I've learned (the hard way #-o  ) to copy files to a practice directory where I can do my worst.  Thanks for the command lines.  I'll give them a whirl.

Bobosity, I'm of similar opinion about man pages.  They are full of useful information _*if*_ you understand them.  I should say comprhend them.  I need man pages that are written in Complete-Linux-Idiot with pictures to get me up to speed. :tongue: 

May I recommend "Beggining Ubuntu Linux" by Keir Thomas.  This is the book that started to unlock Linux for me.  Although it doesn't cover this particular subject of file permissions across the board.:(   I bought two other generic Linux books but they were just like reading the man pages.  I read the words but couldn't comprehend what was being presented.  When I mentioned earlier about needing stuff written in Complete-Linux-Idiot with pictures, that's about how this "Beggining Ubuntu Linux" book starts.  Screen shots of Ubuntu menus/sub-menus/pop-ups/etc., relating to the task that I wanted to accomplish really helped.

One day I'll be a seasoned Linux user and man/info pages will be more useful to me.  Until then I'll need all the help I can get from folks here on UbuntuForums.

Thanks!

---

### Post by fragos on 2006-09-20
Check this one out.  Their sample chapter is very good.  It's available in print or as a pdf download.  "Ubuntu for Non-Geeks" [http://www.nostarch.com/ubuntu.htm](http://www.nostarch.com/ubuntu.htm)

---

### Post by Gotou on 2006-09-21
Thanks fragos!  I'll pop over to Borders this weekend to see if they have it.

---

