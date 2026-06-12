---
title: "Funny terminal command suggestions?"
date: 2009-03-08
forum: General Help
---

### Post by 3dgimp on 2009-03-08
It's my bro's birthday today, and he's a big ubuntu fan. Is there a command I can tell him to run in terminal which has a funny/somewhat geeky outcome?

Ed

---

### Post by Yashiro on 2009-03-08
apt-get moo
telnet towel.blinkenlights.nl

---

### Post by sisco311 on 2009-03-08
cowsay "happy birthday"

---

### Post by 3dgimp on 2009-03-08
cowsay. What a winner. Cheers.

Ed

---

### Post by =CrAzYG33K= on 2009-03-08
> **sisco311 said:**
> cowsay "happy birthday"

Can someone tell me what this does? Coz' I don't have access to my Linux box currently...

---

### Post by Nepherte on 2009-03-08
It shows a cow in the terminal that says Happy Birthday.

---

### Post by sisco311 on 2009-03-08
> **=CrAzYG33K= said:**
> Can someone tell me what this does? Coz' I don't have access to my Linux box currently...

```
 ________________ 
< happy birthday >
 ---------------- 
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

```

---

### Post by lovinglinux on 2009-03-08
> **sisco311 said:**
> cowsay "happy birthday"

Linux is amazing. Someone thinks about a really odd command and there is already an application for it. :D

---

### Post by mhaight on 2009-05-07
```
mhaight@MacPC-Ubuntu:~$ apt-get moo
         (__) 
         (oo) 
   /------\/ 
  / |    ||   
 *  /\---/\ 
    ~~   ~~   
...."Have you mooed today?"...
```

and
```

mhaight@MacPC-Ubuntu:~$ cowsay "happy birthday" 
 ________________
< happy birthday >
 ----------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||
```

Both are pretty good, and funny!

---

### Post by fooman on 2009-05-07
+1 for cowsay...nice!  

and just in time....

```
cowsay "HAPPY MOTHERS DAY"
```

---

### Post by mhaight on 2009-05-08
You can 'Cowsay' anything;
```

root@MacPC-Ubuntu:~# cowsay "<your text>"
 _____________
< <your text> >
 -------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

```

---

### Post by monsterstack on 2009-05-08
Some of my favourites:

```
man woman
```

```
%blow
```

Run these one-by-one:
```
aptitude moo
aptitude moo -v
aptitude moo -v -v
aptitude moo -v -v -v
aptitude moo -v -v -v -v
aptitude moo -v -v -v -v -v
aptitude moo -v -v -v -v -v -v
aptitude moo -v -v -v -v -v -v -v

```

---

### Post by anjilslaire on 2009-05-08
+1 for 
```

man woman

```

---

### Post by mysoogal on 2009-05-08
telnet towel.blinkenlights.nl

shows star wars! in ascii

telnet nerds ! :O

---

### Post by bacardiandwatermelon on 2009-05-08
> **mysoogal said:**
> telnet towel.blinkenlights.nl

shows star wars! in ascii

telnet nerds ! :O

I love it :-)

---

### Post by Greenwidth on 2009-05-08
telnet towel.blinkenlights.nl
Lmao Thats great!

---

### Post by mhaight on 2009-05-08
> **mysoogal said:**
> telnet towel.blinkenlights.nl

shows star wars! in ascii

telnet nerds ! :O

Wow, so good thanks for showing me this!!

---

### Post by mhaight on 2009-05-08
This is the outcome of the aptitude moo thingy

```
root@MacPC-Ubuntu:~# aptitude moo
There are no Easter Eggs in this program.

root@MacPC-Ubuntu:~# aptitude moo -v
There really are no Easter Eggs in this program.

root@MacPC-Ubuntu:~# aptitude moo -v -v
Didn't I already tell you that there are no Easter Eggs in this program?

root@MacPC-Ubuntu:~# aptitude moo -v -v -v
Stop it!

root@MacPC-Ubuntu:~# aptitude moo -v -v -v -v
Okay, okay, if I give you an Easter Egg, will you go away?

root@MacPC-Ubuntu:~# aptitude moo -v -v -v -v -v
All right, you win.

                               /----\
                       -------/      \
                      /               \
                     /                |
   -----------------/                  --------\
   ----------------------------------------------

root@MacPC-Ubuntu:~# aptitude moo -v -v -v -v -v -v
What is it?  It's an elephant being eaten by a snake, of course.
```

---

### Post by Zoowey on 2009-05-08
Is it possible to get cowsay to launch in a terminal whenever you open one and say a predetermined line?

---

### Post by monsterstack on 2009-05-08
> **Zoowey said:**
> Is it possible to get cowsay to launch in a terminal whenever you open one and say a predetermined line?

Sure thing; you can put "cowsay hello" at the very top of your .bashrc file.

```
gedit .bashrc
```

Or if you want the cow to say something different every time, you could put this:

```
cowsay $(fortune)
```

Then you will be greeted by the cow every time you open up a terminal, and he will tell you something interesting each time.

---

### Post by Zoowey on 2009-05-09
> **monsterstack said:**
> Sure thing; you can put "cowsay hello" at the very top of your .bashrc file.

```
gedit .bashrc
```

Or if you want the cow to say something different every time, you could put this:

```
cowsay $(fortune)
```

Then you will be greeted by the cow every time you open up a terminal, and he will tell you something interesting each time.

Thanks a bunch, worked like a charm.

---

### Post by Egi_Power on 2009-05-09
> **monsterstack said:**
> Sure thing; you can put "cowsay hello" at the very top of your .bashrc file.

```
gedit .bashrc
```

Or if you want the cow to say something different every time, you could put this:

```
cowsay $(fortune)
```

Then you will be greeted by the cow every time you open up a terminal, and he will tell you something interesting each time.

Excellent!

Thanks a lot.

Egi_Power

---

### Post by Acapulco on 2009-05-09
That telnet server is amazing!

Cheers for that one.

---

### Post by monsterstack on 2009-05-09
Or if you want your cow to spew Futurama quotes...

```
cowsay $(curl -Is slashdot.org | egrep '^X-(F|B|L)' | cut -d \- -f 2)
```

ought to do it.

---

### Post by ad_267 on 2009-05-09
You don't have to just have a cow saying it:
```
cowsay -f tux "Happy Birthday"
```

Run "cowsay -l" to list all available cows.

---

### Post by monsterstack on 2009-05-09
> **ad_267 said:**
> You don't have to just have a cow saying it:
```
cowsay -f tux "Happy Birthday"
```

Run "cowsay -l" to list all available cows.

I didn't know that. Thanks a lot! I just spent a few minutes playing around with it. Seems like you can make your own cow files. So I made one for Bender the robot from some ascii found [here]("http://www.gotfuturama.com/Multimedia/AsciiArt/dispatch.cgi?target=BenderSulliwan") [gotfuturama.com]. Now you can do it too!

```
gksudo gedit /usr/share/cowsay/cows/bender.cow
```

Then paste the following:

```

$the_cow = <<EOC;
   $thoughts
    $thoughts
     ( )
      H
      H
     _H_
  .-'-.-'-.
 /         \
|           |
|   .-------'._
|  / /  '.' '. \
|  \ \ @   @ / /
|   '---------'
|    _______|
|  .'-+-+-+|
|  '.-+-+-+|
|    """""" |
'-.__   __.-'
     """
EOC

```

Save it and close. Now run

```
cowsay -f bender $(curl -Is slashdot.org | egrep '^X-(B)' | cut -d \- -f 2)
```

for your daily Bender insult.

```

 ____________________________________
/ Bender: I'm tired of this room and \
\ everyone in it!                    /
 ------------------------------------
   \
    \
     ( )
      H
      H
     _H_ 
  .-'-.-'-.
 /         
|           |
|   .-------'._
|  / /  '.' '. 
|    @   @ / / 
|   '---------'        
|    _______|  
|  .'-+-+-+|  
|  '.-+-+-+|         
|    """""" |
'-.__   __.-'
     """  

```

:)

---

### Post by mhaight on 2009-05-09
For a dead cow type:

```
root@MacPC-Ubuntu:~# cowsay -d "Hello World"
 _____________
< Hello World >
 -------------
        \   ^__^
         \  (xx)\_______
            (__)\       )\/\
             U  ||----w |
                ||     ||

```

---

### Post by mhaight on 2009-05-09
> **monsterstack said:**
> I didn't know that. Thanks a lot! I just spent a few minutes playing around with it. Seems like you can make your own cow files. So I made one for Bender the robot from some ascii found [here]("http://www.gotfuturama.com/Multimedia/AsciiArt/dispatch.cgi?target=BenderSulliwan") [gotfuturama.com]. Now you can do it too!

```
gksudo gedit /usr/share/cowsay/cows/bender.cow
```Then paste the following:

```

$the_cow = <<EOC;
   $thoughts
    $thoughts
     ( )
      H
      H
     _H_
  .-'-.-'-.
 /         \
|           |
|   .-------'._
|  / /  '.' '. \
|  \ \ @   @ / /
|   '---------'
|    _______|
|  .'-+-+-+|
|  '.-+-+-+|
|    """""" |
'-.__   __.-'
     """
EOC

```Save it and close. Now run

```
cowsay -f bender $(curl -Is slashdot.org | egrep '^X-(B)' | cut -d \- -f 2)
```for your daily Bender insult.

```

 ____________________________________
/ Bender: I'm tired of this room and \
\ everyone in it!                    /
 ------------------------------------
   \
    \
     ( )
      H
      H
     _H_ 
  .-'-.-'-.
 /         
|           |
|   .-------'._
|  / /  '.' '. 
|    @   @ / / 
|   '---------'        
|    _______|  
|  .'-+-+-+|  
|  '.-+-+-+|         
|    """""" |
'-.__   __.-'
     """  

```:)

Thanks!! I tried it:

```
root@MacPC-Ubuntu:~# cowsay -f bender $(curl -Is slashdot.org | egrep '^X-(B)' | cut -d \- -f 2)
 ________________________________________
/ Bender: Professor! Make a woman out of \
\ me!                                    /
 ----------------------------------------
   \
    \
     ( )
      H
      H
     _H_
  .-'-.-'-.
 /         
|           |
|   .-------'._
|  / /  '.' '. 
|    @   @ / /
|   '---------'
|    _______|
|  .'-+-+-+|
|  '.-+-+-+|
|    """""" |
'-.__   __.-'
     """
```

---

