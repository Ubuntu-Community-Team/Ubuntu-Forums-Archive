---
title: "Permission denied again"
date: 2006-07-26
forum: Desktop Environments
---

### Post by AsRock on 2006-07-26
Hello,

Starting last night i started to get Permission Denied again.  Is there a way that would make me administrator so i can temperly get past it so i can run my program again.

would is be usefull to post the whole script i am using here ?

Only part i can see in the script that is not in the server game folder is nohup </dev/null >/dev/null $0 watchdog &

More info

I'm trying to run a Operation Flashpoint server.  It was running mid yesterday and last night it started to say  Permission Denied.  As far as i know nothings been changed any idea's ?

Sorry found my origanel link from last week.
[http://www.ubuntuforums.org/showthread.php?p=1302191#post1302191](http://www.ubuntuforums.org/showthread.php?p=1302191#post1302191)

Thank You....

---

### Post by cilynx on 2006-07-26
I know that sudo sometimes runs into problems when it comes to redirection and piping of output (which is what is going on in that line).  I didn't figure it would happen inside of a script though.  

What happens if you 'sudo -s' to get yourself a root prompt, and then './ofpserver' from there?

---

### Post by AsRock on 2006-07-26
Well i guess i would have to put the whole path in to do it from root.  Worth a try though.

Thing is about sudo i was not using or even need to use it then suddenly BUMP  Permission denied.  Thats when i thought i'd try it and still not work.

---

### Post by AsRock on 2006-07-26
Well i just tryed sudo -s -H  which gave me root so i cd .. to needed folder and just says same thing.  If i try ./ofpserver start i get the Permission denied.  If i put sudo at the start it says command not found.

Thanks for your reply :):)

---

### Post by cilynx on 2006-07-26
As mentioned in previous posts, it sounds like some file permissions got messed up somewhere along the lines.  You can get "Permission Denied" for trying to execute a file that you don't have permission to because it is owned by someone else.  You can also get it if you try to execute a file that is owned by you, but set non-executable.  

Really bad troubleshooting idea:

(Yes, I know this is a really bad idea.  Yes, I know I shouldn't be telling the random folks on the forums to do this.  That doesn't make it not work...)

Start with the script itself, then move on to things it references.  Set the permissions on things that need to be run to 777.  (777 is read, write, and exec by --anyone--)  Try running the script between each set.  Once the script stops complaining, you've found your problem.

Remember when doing this kind of thing that you are destroying the very fabric that makes *NIX stable and secure whereas Win* isn't.  Write down the permissions of files before you change them so that you can put them back when you're done.  When you find your problem, play around and set it to the lowest possible permission to get it to run.

There are many tutorials on file permissions out there.  Prolly wouldn't hurt to read a couple.

Best of luck --

---

### Post by endfx on 2006-07-26
Well if you want admin, you could just do a:
$> sudo bash

which would give you root, then run the script.

But yeah, it sounds like a permission error on the files or directories that you should check first.

---

### Post by AsRock on 2006-07-26
Yeah it was  a file.  Kinda odd really as none of them were changed  by me Hmm.


Thank You all for your help :) :) :) :)

And thanks for the $> sudo bash command.

---

