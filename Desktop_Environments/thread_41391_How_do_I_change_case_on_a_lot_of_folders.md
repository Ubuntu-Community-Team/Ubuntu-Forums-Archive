---
title: "How do I change case on a lot of folders?"
date: 2005-06-13
forum: Desktop Environments
---

### Post by paretooptimum on 2005-06-13
Hi,

I have a folder of folders:

Folder A
folder b
FOLDER C
...
Folder Z

I want to normalise them all to:

folder a
folder b
folder c
...
folder z

Who wants to be the first one to tell me how to do this quicklly and painlessly?

---

### Post by GrammatonCleric on 2005-06-13
Here's a little perl script that I wrote for my my mp3 collection.  It will rename files and directories in lower case and also replace spaces in names with an under score.

So a directory named "The Grand Design"  will become "the_grand_design."
Also all sub files will be named the same way. 

If you wish to do so copy the following to a file...


#!/usr/bin/perl


#chdir ("");

&traverse('.');

sub traverse {
    local($dir) = shift;
    local($path);
    unless (opendir(DIR, $dir)) {
        warn "Can't open $dir\n";
        closedir(DIR);
        return;
    }
    foreach (readdir(DIR)) {
        next if $_ eq '.' || $_ eq '..';
        $path = "$dir/$_";
        if (-d $path ) {         
	  &lc;
            &traverse($path);
        } 
        elsif (-f _) 
        { 
          &lc;
        }
    }
    closedir(DIR);
}

sub lc
{           $file = $_;
           $file = "\L$file\E";
           $file =~ s/ /_/g;
           if ($file ne $_)
           {
             print "renamed $_ to $file\n";
             `mv \"$dir/$_\" \"$dir/$file\"`;
           }
	    $path = "$dir/$file";

}



Copy or move the script file to where you what to lower case.  As an exmaple this is where I placed the my script for my mp3 collection.  

lc.pl is the script.

[http://linuxjunkie.net/images/Screenshot.png](http://linuxjunkie.net/images/Screenshot.png)


To execute the script drop into a terminal and cd into the path where you copied the script.  Then type perl lc.pl.   

[U]
[B]MAKE SURE THAT YOU WANT TO RENAME ALL SUB FILES AND DIRECTORIES!!!!
[/B][/U]

G

---

### Post by ubuntu_demon on 2005-06-13
I moved this thread.

please look where to post before posting

---

### Post by paretooptimum on 2005-06-13
GrammatonCleric:

What is the argument for using "_" instead of " " when naming music files?

If you ever used a tag editor to clean up your files - ie sync the song title with the tag - you would end up with your tags in muine/rhythmbox looking like "the_rolling_stones" instead of "the rolling stones".

What am I missing? How do I change the script if I don't want this outcome?

EDIT: Sorry I was thinking of music files, not music folders. I'll still ask the question: why name folders with no "real" spaces?

EDIT2: Request: I've run the script and it worked great. I'm still warm and cold on "_" instead of " ". Can you write me a script to swap them back? That way I can back out gracefully if it doesn't grow on me. 

Question: Is there a good/easy online resource to learn perl? This doesn't look too hard, I just need some basics.

demon - sorry, but maybe I was going to add the words "HOWTO" to the front of my post ;)

---

### Post by ubuntu_demon on 2005-06-13
[QUOTE=paretooptimum]GrammatonCleric:

What is the argument for using "_" instead of " " when naming music files?

If you ever used a tag editor to clean up your files - ie sync the song title with the tag - you would end up with your tags in muine/rhythmbox looking like "the_rolling_stones" instead of "the rolling stones".

What am I missing? How do I change the script if I don't want this outcome?

EDIT: Sorry I was thinking of music files, not music folders. I'll still ask the question: why name folders with no "real" spaces?

demon - sorry, but maybe I was going to add the words "HOWTO" to the front of my post ;)[/QUOTE]
 only write an howto after the problem is solved if you think others can profit from it :)

---

### Post by ow50 on 2005-06-13
Answering the original question:
```
#!/bin/bash

find * -type d |
while IFS= read -r i; do
	rename 's/([[:upper:]])/\l$1/g' "$i"
done
```
You have to run that script once for each level of subdirectories.

---

### Post by 23meg on 2005-06-13
does anyone know of a general purpose gui renaming utility?

---

### Post by paretooptimum on 2005-06-13
Yea, I'm going to add that the projected problem has happened:

EasyTag now thinks every tag needs to be fixed...

[http://www.coriolisresearch.com/the_problem.png](http://www.coriolisresearch.com/the_problem.png)

All new question: can someone write me a script to change all my folders and file names and replace "_" with " "?

I need a smiley with me hitting myself on the head with a bat.  :-P

---

### Post by ow50 on 2005-06-13
[QUOTE=paretooptimum]All new question: can someone write me a script to change all my folders and file names and replace "_" with " "?[/QUOTE]
Changes are simple to the script I posted before, if you know some find syntax and Perl style regular expressions.
```
#!/bin/bash

find * |
while IFS= read -r i; do
	rename 's/_/ /g' "$i"
done
```
Again, you have to run that script once for each level of subdirectories.

---

### Post by Dave_is_sexy on 2005-06-13
There's a smiley of hitting your head on a wall...  ](*,)

---

### Post by paretooptimum on 2005-06-13
Its not really hitting your head on the wall,  ](*,)  ,  which I take to mean "I can't solve the problem" but rather I ignored the warning and did it anyway "hitting yourself on the head"  [-X

---

### Post by anatole on 2005-06-14
a command that will rename the subdirectories and files inside them in the directory you are standing is:

find . -type d -exec rename 'y/A-Z/a-z/' {} \;

my friend suggested it, so i don't know how it works :D but it works... drops some errors but does the job :) already tried that.

---

### Post by ow50 on 2005-06-14
[QUOTE=anatole]a command that will rename the subdirectories and files inside them in the directory you are standing is:

find . -type d -exec rename 'y/A-Z/a-z/' {} \;[/QUOTE]
That's pretty much same as the script I posted, except, if I remember correctly [:upper:] is locale dependent and should detect more than the ascii range A-Z.

---

