---
title: "Renaming m4a to mp4 script?"
date: 2005-01-25
forum: Desktop Environments
---

### Post by Sophisto on 2005-01-25
Hi! I don't know much about how to write scripts for the shell so maybe some of you could help me out with this;

I have a 20gb collection of m4a files (in various subdirectories) that I need to rename to mp4.

This, since Amarok wont play them - and I would really like to continue using Amarok.

Thanks a lot

---

### Post by piedamaro on 2005-01-25
rename m4a mp4 *m4a

---

### Post by Sophisto on 2005-01-25
finn@ubuntu:~/music/tmp/ABC/The Lexicon of Love $ rename m4a mp4 *m4a
Bareword "m4a" not allowed while "strict subs" in use at (eval 1) line 1.

Any idea why?

---

### Post by crun on 2005-01-25
You might also want to look at the excellent [KRename](http://www.krename.net/). KDE app but works perfectly in Gnome.

It's not in the Warty repositories, but you can download an older deb from their [SourceForge project page](http://sourceforge.net/project/showfiles.php?group_id=42805&package_id=43183)

---

### Post by piedamaro on 2005-01-25
Dunno, it works here. However there is a very simlar thread, it seems that rename doesn't work atm. [http://www.ubuntuforums.org/showthread.php?t=12547](http://www.ubuntuforums.org/showthread.php?t=12547)

---

### Post by valadil on 2005-01-25
for i in `ls *.m4a` ; do mv $i `echo $i | sed -e 's/.m4a/.mp4/'` ; done

This line will move all m4a files in the current directory to mp4.

In case anyone cares, I will now break down what the above line does.

First off, the backticks ` and it's counterpart, `.  These are not stylistic apopstrophes.  They have a different function.  When used on a commandline, the commands in the backticks is executed and used as an argument.  The first command we are backticking is ls *.m4a.  This returns all .m4a files in the directory.  

for i in, will see the list of m4a files.  For is kind of interesting.  If you've ever programmed before you probably have a good idea of what it does.  If not, I really don't want to go into any depth on it right now.  Sorry.  Needless to say, it will go through all the arguments after in, (in this case everything returned as an m4a file) and treat those as $i (when you assign a variable in bash it's ust the variable, afterwards when you call it it gets a dollar sign prefix) for all the commands between do and done.

Next up is a semicolon.  This ends the current command as if it were a line break.  After that comes do.  This starts the commands that are part of the for loop.

Finally we get to renaming the file.  mv is used to move files around.  It seems unintuitive, but this is the same as renaming a file.  To use it we write mv the_file_to_rename its_new_name.  $i is going to be the file in question.  For will fill this in with each of the m4a files one at a time and do the command for each of the files.  

Now we get to the hard part.  Sed is a tool for parsing text.  You may notice that once again we use backticks here.  What we're doing is saying execute this command, and the result will be the new name of the file.  

The first command in the backticks is echo.  It print stuff to the screen.  In this case we're printing the name of the file we're working with.  After that comes a pipe, |.  This says that instead of printing the result of the last command to the screen, we take it into the next command.  sed sees the name of the file and evaluates a sed command on it.  -e, by the way, is what says evaluate.  s says that we are replacing parts of the string.  The next slash indicates that what follows, .m4a, is what will be replaced.  The slash after that ends the replacee and begins the replacer.  In this case we're replacing it with .mp4.  The slash after that ends the replacee and allows for more commands.  After that, we end the sed evaluation, end the backtick, watch sed return the new filename, end that command with a semicolon, then tell for that we are done.

How is that for way more information than you asked for?

---

### Post by martijntje on 2005-01-25
[QUOTE=valadil]for i in `ls *.m4a` ; do mv $i `echo $i | sed -e 's/.m4a/.mp4/'` ; done

This line will move all m4a files in the current directory to mp4.

In case anyone cares, I will now break down what the above line does.

First off, the backticks ` and it's counterpart, `.  These are not stylistic apopstrophes.  They have a different function.  When used on a commandline, the commands in the backticks is executed and used as an argument.  The first command we are backticking is ls *.m4a.  This returns all .m4a files in the directory.  

for i in, will see the list of m4a files.  For is kind of interesting.  If you've ever programmed before you probably have a good idea of what it does.  If not, I really don't want to go into any depth on it right now.  Sorry.  Needless to say, it will go through all the arguments after in, (in this case everything returned as an m4a file) and treat those as $i (when you assign a variable in bash it's ust the variable, afterwards when you call it it gets a dollar sign prefix) for all the commands between do and done.

Next up is a semicolon.  This ends the current command as if it were a line break.  After that comes do.  This starts the commands that are part of the for loop.

Finally we get to renaming the file.  mv is used to move files around.  It seems unintuitive, but this is the same as renaming a file.  To use it we write mv the_file_to_rename its_new_name.  $i is going to be the file in question.  For will fill this in with each of the m4a files one at a time and do the command for each of the files.  

Now we get to the hard part.  Sed is a tool for parsing text.  You may notice that once again we use backticks here.  What we're doing is saying execute this command, and the result will be the new name of the file.  

The first command in the backticks is echo.  It print stuff to the screen.  In this case we're printing the name of the file we're working with.  After that comes a pipe, |.  This says that instead of printing the result of the last command to the screen, we take it into the next command.  sed sees the name of the file and evaluates a sed command on it.  -e, by the way, is what says evaluate.  s says that we are replacing parts of the string.  The next slash indicates that what follows, .m4a, is what will be replaced.  The slash after that ends the replacee and begins the replacer.  In this case we're replacing it with .mp4.  The slash after that ends the replacee and allows for more commands.  After that, we end the sed evaluation, end the backtick, watch sed return the new filename, end that command with a semicolon, then tell for that we are done.

How is that for way more information than you asked for?[/QUOTE]
 Valadil, that's really nice. However, it doesn't really work when you have files with spaces in them.

Yes, i know that you're not * supposed * to have files with spaces. IT'S NOT MY FAULT, boohoo, it's all those stupid people that post in newsgroups...

Do you maybe know of a way to make ls escape spaces in filenames?

---

### Post by valadil on 2005-01-26
Whoops, forgot about that.  That's what happens when I do tech support in class.

Try replacing ls *.m4a with 
ls *.m4a | sed -e 's/ /\\ /g'

Sadly, the for loop doesn't seem to care.  I did manage to escape the spaces though...

This is the part where I don't know the "correct" way to fix things but I can offer scripting support that will probably help anyway.

You'll notice that ls returns files in lines.  So we need to loop through the ls and grab each line instead of each file.  To make this loop  though, we need to count how many lines there are.  The best way to do this is with wordcount, wc.  wc -l will count lines.

ls | wc -l
This returns how many lines we have.

Isolating the nth line of text is something that took me way too long to figure out how to do.  I use a couple commands for this.  head returns a number of lines from the top of a file and tail returns a number of lines from the bottom.  n lines from the top piped into 1 line from the bottom gives us the nth line.

So let's try something like this.

for i in ` seq \`ls *.m4a | wc -l \`` ; do mv `ls *.m4a | head -n $i | tail -n 1` `ls *.m4a | head -n $i | tail -n  | sed -e 's/.m4a/.mp4/g' ` ; done

FWIW that has to be the single ugliest line I've ever written.  Hope it works, I have no desire to test it on my collection.

Actually I tested everything except the moving.  I think it'll work.  BTW, seq returns all the numbers from 1 to a number specifed.  So instead of looping for 5, we loop for 1 2 3 4 5.  seq is my friend.

---

### Post by Sophisto on 2005-01-26
Sorry but when I tried I got the following message? Do I need to create a special directory for the new files to be created??


finn@ubuntu:~/music/tmp/ABC/The Lexicon of Love $ for i in ` seq \`ls *.m4a | wc -l \`` ; do mv `ls *.m4a | head -n $i | tail -n 1` `ls *.m4a | head -n $i | tail -n | sed -e 's/.m4a/.mp4/g' ` ; done
tail: option requires an argument -- n
Try `tail --help' for more information.
mv: when moving multiple files, last argument must be a directory

Thanks

---

### Post by matid on 2005-01-26
Mass changing of file name with 'rename' tool:
rename "y/m4a/mp4/" *

Unfortunately it works in current directory.

---

### Post by piedamaro on 2005-01-27
[QUOTE=matid]Mass changing of file name with 'rename' tool:
rename "y/m4a/mp4/" *

Unfortunately it works in current directory.[/QUOTE]
 Did rename behaviour change? Why rename m4a mp4 *m4a is working for me in fedora but not in ubuntu? (Sophisto, sorry for that, I've tried it in fedora only ;) )

The space-in-filename issue is plaguing me as well, I couldn't get to work the script for mounting isos at gnome-hacks :(

---

### Post by Sophisto on 2005-01-28
Dont worry... in the end I just booted mandrake and installed krenamer and that was it... Unfortunately I realised that Amarok wont read the id3 tags in the mp4 files.. so Ill probably have to convert the 20gb to mp3 anyway....

---

