---
title: "Working with Perl on 8.10"
date: 2009-06-23
forum: General Help
---

### Post by cloudfrog on 2009-06-23
Hey everyone!

I'm starting to get into the more interesting aspects of running a Linux-based OS, having recently become more acquainted with Bash.  I'd like to continue progressing, and I find Perl pretty interesting from a programming standpoint.  I know that many Linux distros come with the Perl and a compiler, and would like to know if this applies to Ubuntu 8.10 as well.  Any additional help or resources would be very appreciated!

Thanks everyone, you've been great!

---

### Post by nice_like_rice on 2009-06-23
Yes, perl is included in Ubuntu. You can call the interpreter by typing "perl" followed by the filename eg "helloworld.pl". Where you go from there is up to you :), if you are comfortable using the command line, I highly recommend "vim" for editing scripts, otherwise there are plenty of good IDE's out there.

(you must do "sudo apt-get install vim" - the default version of vim included in ubuntu is a smaller version of it without syntax highlighting)

david

---

### Post by jonobr on 2009-06-23
Perl is the daddio.....


I would recommend a few things for you,

Perl is installed by default in ubuntu,

You can find out where its installed by running 

```
which perl
```
That done, you can create your first perl program, by opening a text editor
eg gedit, and create a file <file1>
and type 
```

#!/usr/bin/perl
print "Hello World!\n";

```

Save the file,

change its permission so you can run it.
```
chmod 755 file1
```

and then execute it
```
./file1
```

Presto, your first perl program.

BUT MAN IT CAN DO SO MUCH MORE!!!!
And its easy to do simple things , however, it can get very confusing and tough when you start using regular expressions subroutines and so on.

You could try some of the tutorials, but I would really recommend getting a book like learning perl from Oreilly.
I think they do a great job of putting it all together.

Your also going to have to become familiar with CPAN.

This is the Comprehensive Perl archive network.

People upload modules into CPAN which you can reuse in your program so you dont have to reuse the wheel.
FOr example, if your perl program requires you to do an SNMP query, you can invoke such a module which you can get on CPAN to do that ofr you without you needing to reinvent the wheel.

You can also get Perl for different OS's as well as the latest build itself.

Lastly, I would recommend if you run into issues, post over in the programming section as the general help probably will not get many responses to questions.


I have been in a lot of bad situations needing to do something and Perl has saved the day for me on more then one occasion, anyway, Im babbling.

Best of luck

---

### Post by cloudfrog on 2009-06-23
> BUT MAN IT CAN DO SO MUCH MORE!!!!
And its easy to do simple things , however, it can get very confusing and tough when you start using regular expressions subroutines and so on.

Haha, I should hope it can do more than a Hello World! script!  Hehe...

> You could try some of the tutorials, but I would really recommend getting a book like learning perl from Oreilly.
I think they do a great job of putting it all together.

Oh, good...that's the exact book I got.  :)


Thank you both for your quick and helpful responses!  I just wrote my first script in the Vim editor, and it looks great.  I'm really excited about this!

---

### Post by jonobr on 2009-06-23
Nope actually hello world is about as deep as it goes..........:-)

I figured you were taking your first step, but given you mentioned you have done some bash scripting, I think I should re-dit my post.:P

Makes you look like a newb, which of course your not...

PS 

```
Hello Perl
```

---

### Post by cloudfrog on 2009-06-23
Haha, don't get me wrong, I most certainly am a Perl newb.  :)  I'm starting with the absolute basics...you know how it goes.  New language, new string of Hello World! scripts and Speed Limit Citation calculators...

Like I said, you've all been very helpful, and I appreciate your responses!

I should be writing endless-loops and OS-crashing scripts in no time!  :-D

---

