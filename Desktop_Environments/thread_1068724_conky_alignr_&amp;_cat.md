---
title: "conky alignr &amp; cat"
date: 2009-02-13
forum: Desktop Environments
---

### Post by tears.of.angels on 2009-02-13
hey everyone, i've been racking my brain trying to get conky to align something to the right.

the problem is i want to cat a todo list like so:
```
${alignr}${execi 30 cat /home/andrew/.scripts/todo}
```

but when that gets run, only the first line is aligned to the right, and the rest are left aligned.
is there a bracket wrong somewhere, or is there a global "always align right" that i can set up for my script that i was not aware about?

---

### Post by rrplay on 2009-02-25
> **tears.of.angels said:**
> hey everyone, i've been racking my brain trying to get conky to align something to the right.

the problem is i want to cat a todo list like so:
```
${alignr}${execi 30 cat /home/andrew/.scripts/todo}
```

but when that gets run, only the first line is aligned to the right, and the rest are left aligned.
is there a bracket wrong somewhere, or is there a global "always align right" that i can set up for my script that i was not aware about?

maybe this can help you out look here 
[http://lifehacker.com/5067341/customize-conky-for-ambient-linux-productivity]("http://lifehacker.com/5067341/customize-conky-for-ambient-linux-productivity")    see ${execi 30 cat /home/username/Desktop/TODO.txt | fold -w40 }

---

### Post by tears.of.angels on 2009-02-26
thanks for the tip, but fold doesn't do what i want, i don't have any long lines, they're just aligned right.

i've attached a pic of what it looks like. the first line is aligned right and the rest are at the left of the window. it looks gross.

anyone every dealt with this problem before?

---

### Post by rrplay on 2009-02-26
thanks for the pic to see 

ok which version of conky ??  and so you have curl installed ?? and are you launching conky from a terminal to view info ? this troubleshoot can get you conky crazy so check for curl package installed and try the previous fold did you use see ${execi 30 cat /home/username/Desktop/TODO.txt | fold -w40 } as .txt because you originally had /home/andrew/.scripts/todo   so if poss post the actuall line you tried with fold

 then test out option own_window_type override   to "normal"..
not sure about this one  ${execi 2 less /wherever/todo.txt}

when I have a bit of time later I'll see about a todo list on mine and post back.

---

### Post by rrplay on 2009-02-26
ok look here >> [http://ubuntuforums.org/showthread.php?t=733959](http://ubuntuforums.org/showthread.php?t=733959)

and I made todo file like this
 To Do
${hr}
${color 99FF99}$alignr${font Verdana:style=Italic:size=9}${exec cat /home/wherever/todo-test.txt}



also on the page see execi  for "interval info"  i used spacebar to display alignment or you can exec cat to a seperate screen with the buffer alignmnet

you should be AOK now

---

### Post by tears.of.angels on 2009-02-26
well i have version 1.6.1 of conky, i don't know what you want me to do with curl, but i've had it installed the whole time.

and the command you gave me is the same as the one i'm using, i want mine aligned to the right, and yours looks like it's aligned to the left.
it's wierd, because mine aligns the first line to the right and the rest are left aligned. 

i was just thinking, is there a way to put all my todo's on a single line with a line break symbol like this:

```
do this $ do that $ do something else
```

so the text file is on a single line, then have a command break it into separate lines that are aligned right?
i don't know, just spitballing.

thanks for all the help up to this point, i really appreciate it!

---

### Post by rrplay on 2009-02-27
ok  here you go!! if you just need the just command only use this:

${exec cat /home/wherever/todo-test.txt}

look at the txt file and you may have to adjust the spacing to fit as well as maybe adjust your maximum_width 250 [mine was 250 and you may want to play around a bit with text_buffer_size 2048 {more in other posts about this}with the screenshot included 

review you info here and you might as well read about tail [http://conky.sourceforge.net/conkyrc-vert]("http://conky.sourceforge.net/conkyrc-vert") see the screenshot and txt file.

 if you need more help post the conkyrc in [http://ubuntuforums.org/showthread.php?t=281865]("http://ubuntuforums.org/showthread.php?t=281865") you have a solution now

---

### Post by tears.of.angels on 2009-02-27
thanks for the help, but still not what i want.

just to be clear, i did a mock-up of what i want it to look like.
the very bottom has the mocked-up text; that's how i'd like it to look.

the text just above it is still what it's doing, aligning the first line of the text file to the right, and the rest to the left

---

### Post by rrplay on 2009-02-28
this is probably what you are going to have to do to get the look that you want...look here [http://linux-hardcore.com/index.php?topic=1879.0]("http://linux-hardcore.com/index.php?topic=1879.0") for the 'todo' conkyrc 
  note that it is 
> ${execi 2 less /home/wherever/todo.txt} and simply make your todo list however you want and position it  wherever you want !! 'modular conky'  you will now have to run 2 instances of conky 
  read here: [http://ubuntuforums.org/archive/index.php/t-1036707.html]("http://ubuntuforums.org/archive/index.php/t-1036707.html") unless you already now how to do this..see the last post for autostart info for your system .

---

### Post by jjgomera on 2009-02-28
> **tears.of.angels said:**
> hey everyone, i've been racking my brain trying to get conky to align something to the right.

the problem is i want to cat a todo list like so:
```
${alignr}${execi 30 cat /home/andrew/.scripts/todo}
```

but when that gets run, only the first line is aligned to the right, and the rest are left aligned.
is there a bracket wrong somewhere, or is there a global "always align right" that i can set up for my script that i was not aware about?

hi, this must work:

${execpi 30 cat /home/andrew/.scripts/todo | sed s/^/\${alignr}/ }

---

### Post by rrplay on 2009-03-02
jjgomera   way to go !! that's it !! solves tears.of.angels alignment perfectly...
 > hi, this must work:
${execpi 30 cat /home/andrew/.scripts/todo | sed s/^/\${alignr}/ } 

works perfectly !! and the proof is here:

---

### Post by tears.of.angels on 2009-03-02
wow, thanks jjgomera!

i don't know why i didn't think of using sed, but i'm glad you figured it out!

thanks so much, an aesthetic issue fixed!

:biggrin:

---

### Post by mobilediesel on 2009-03-02
> **jjgomera said:**
> hi, this must work:

${execpi 30 cat /home/andrew/.scripts/todo | sed s/^/\${alignr}/ }

I can't believe I didn't think of sed! I tried that before, now I gotta remember what I wanted aligned to the right...

---

