---
title: "Astronomical gear train/gear ratio calculation tool for linux?"
date: 2010-05-11
forum: Education &amp; Science
---

### Post by BastardNamban on 2010-05-11
I already searched through all the stickies and program database for anything I thought might help me, and found nothing I can figure will, so I'm asking here.

I am looking to plan out some special clocks, and while I know what ends I need to achieve, I don't know of any program for linux 
that could help me calculate the special gear train ratios I need.

See, these are going to be astronomical clocks, for my own personal use. They involve some more complicated gear ratios that are non-standard, 
and thus, not easy for me to calculate without software- I can, but it is arduous to say the least.

For example, I'm trying to make a new solar-sidereal gear train, and need to create a gear ratio of exactly 1:1.0027379. 
I know others have done this with between 4-20 some odd gears, but I need to create something new.

Basically, what I need is something that can take a given final ratio, and show me what in whole numbers in the form of fractions
what numbers for a given number of gears can make the ratios I need.

For example, here's a version of what watchmaker Breguet came up with:

(51 teeth/82 teeth) x (79 teeth/49 teeth) = 1: 1.00273768 (solar:sideral ratio; the true ratio for the spacial relation is 1:1.0027379)

Using that kind of clockmaker's layout, I need something that can help me calculate for, given the number of fractions (each a gear and pinion combo) 
I choose to use, and a final given ratio, whole numbers that will produce the result.

I'm sure this would be simple for some sort of existing software, probably some form of spreadsheet calculation, but I am a novice in such matters, 
and am not sure what would work best for this.

Can anyone point me in the right direction for what can do this? Any sort of astronomical phenomena calculation program suggestions would be welcome too. 
I just haven't been able to find much despite looking for a few years on and off now!

---

### Post by radioboy on 2010-05-20
Looks like some sort of constrained optimization problem...
Check here: [http://wiki.cacr.caltech.edu/danse/index.php/Optimization_Algorithms](http://wiki.cacr.caltech.edu/danse/index.php/Optimization_Algorithms)

---

### Post by BastardNamban on 2010-06-08
Thanks for the reply, but I have no idea whatsoever what anything on that page can do for me.

I understand what an optimization problem is, and I agree- but finding a way to implement such a layout in software is what confuses me.

Any mathematicians out there that can sugguest a simple solution for something like this? A program that solves for ratios with a simple fractional layout like that listed above would be a huge boon to clockmakers. That layout is needed for us to do whole number gears in proper ratios.

---

### Post by oldfred on 2010-06-10
[ATTACH]159927[/ATTACH]I created a brute force try all combinations and only print out the ones with small error. It trys all gears in a range so for a set you get your answer 4 times as each gear can be 51, each gear can be 82 etc.

I print calculated ratio, error, and the four gears.  You will see all those with exponent of 7 are the same four gears. I am trying to teach myself python so I do not expect this to be considered "good" code.

fred@fred-desktop:~/Projects/PyAssetTrakkr$ python clockgear.py
1.00273768044 2.19561971271e-07 51.0 79.0 49.0 82.0
1.00273768044 2.19561971271e-07 51.0 79.0 82.0 49.0
1.00273972603 1.82602739729e-06 54.0 61.0 45.0 73.0
1.00273972603 1.82602739729e-06 54.0 61.0 73.0 45.0
1.00273972603 1.82602739729e-06 60.0 61.0 50.0 73.0
1.00273972603 1.82602739729e-06 60.0 61.0 73.0 50.0
1.00273972603 1.82602739729e-06 61.0 54.0 45.0 73.0
1.00273972603 1.82602739729e-06 61.0 54.0 73.0 45.0
1.00273972603 1.82602739729e-06 61.0 60.0 50.0 73.0
1.00273972603 1.82602739729e-06 61.0 60.0 73.0 50.0
1.00273972603 1.82602739729e-06 61.0 66.0 55.0 73.0
1.00273972603 1.82602739729e-06 61.0 66.0 73.0 55.0
1.00273972603 1.82602739729e-06 61.0 72.0 60.0 73.0
1.00273972603 1.82602739729e-06 61.0 72.0 73.0 60.0
1.00273972603 1.82602739729e-06 61.0 78.0 65.0 73.0
1.00273972603 1.82602739729e-06 61.0 78.0 73.0 65.0
1.00273972603 1.82602739729e-06 66.0 61.0 55.0 73.0
1.00273972603 1.82602739729e-06 66.0 61.0 73.0 55.0
1.00273972603 1.82602739729e-06 72.0 61.0 60.0 73.0
1.00273972603 1.82602739729e-06 72.0 61.0 73.0 60.0
1.00273972603 1.82602739729e-06 78.0 61.0 65.0 73.0
1.00273972603 1.82602739729e-06 78.0 61.0 73.0 65.0
1.00273768044 2.19561971271e-07 79.0 51.0 49.0 82.0
1.00273768044 2.19561971271e-07 79.0 51.0 82.0 49.0
done

  Newer version info several posts down updated Jun16 2010

---

### Post by BastardNamban on 2010-06-11
Oldfred, thank you very much! What program did you use to do this?

It looks like you found a way to use the same 4 numbers, in different orders, to come up with the first number, the ratio. Then what is the second decimal number
each time? (ie: in 1.00273768044 2.19561971271e-07 51.0 79.0 49.0 82.0, the 2.19561971271e-07 part.)

It's crucial that I use whole numbers only for the gears in the sequence.
Also, I need that exact end ratio, and I'm willing to not limit myself to 4 gears- up to 20, if need be. More accurate is better.

Finally, the 4 gears I used above aren't quite accurate- they were the ones Breguet used (I gave them only as an example, I would not use the same solution as he), and his train was off by 10 seconds or so a year, I believe.

Much higher levels of accuracy are obtainable, but more gears must be used.

I really appreciate you trying whatever you did, and I'd like to know what you used. I'd like to learn how to use it, and continue on my own with even more gears!

Finally, is there a way to make a gui program to calculate gear ratios in this way for clockmakers/watchmakers (ie: gear tooth numbers in whole numbers only for a desired result)? I would think linux can do it- I'd just need someone to make it for me. Can I pay someone to make a program to do this? I would!

---

### Post by oldfred on 2010-06-11
The second value is error, you see it changed to exponential since it was so small.  Whatever simple logic I used only gave errors to 6 or 7 decimals.

I attached the program, it is just python. copy it to your system and make it executeable. I had it in desktop so I changed to this:

fred@fred-desktop:~$ python clockgear.py

This only uses 2 gears sets and when I had 0 to 100 on all 4 it took forever to run. It would be relatively easy to add more but may take too long to run. not sure how to add optimization to make it easier to run.

Look at program, it is short enough to understand I think for just about anyone as it is not complex.

---

### Post by BastardNamban on 2010-06-11
Fred, I truly appreciate your help. Forgive me for 2 things, though-

1. I assume there is a way through terminal to assign a file transfer from a networked computer for your file- as nothing is attached as a file to your message in any normal sense to me as a downloadable link.

2. I've never used or see one, but I assume your file by the file name is a "Python script". I have no clue how scripts work or how to use them- it's been one of the key mysteries to me as to how/what linux is. It's like trying to understand a facet of God or something, you have no clue how to wrap your head around it until someone explains something about it to you. If it is one of these "scripts", where should I look to learn how to use it? I'm sorry, while I'm experienced for a few years now with linux, there are some areas I know nothing about- scripts are one of the biggest areas for me.

Thanks.

---

### Post by oldfred on 2010-06-11
In post #4 at the bottom is clockgear.py which if you click on it you can download it. It is a simple python script. If you click on it it should open to edit so you can see it. If you right click you can change the property to executeable.

---

### Post by BastardNamban on 2010-06-11
Ok, I have it and changed it's properties to run as an executable.

If this is a script, I think I see what they are now. It's preconfigured computer language to do something, 
and you edit it to do what you want with certain values. Then terminal runs it and gives you useful output.

Ok, here goes:

1. Assuming I can indeed edit this, could I change the line of
```
#calc_ratio = (wheel1 * wheel2 ) / (pinion1 * pinion2)
```
to this instead:
```
#calc_ratio = [(wheel1 / pinion1) * ( wheel2 / pinion2)]
```?

And if I can, could I add more wheels & pinions if I want to try, in this form:```
#calc_ratio = [(wheel1 / pinion1) * ( wheel2 / pinion2) * (wheel3 / pinion3) * -ETC-]
```?

2. I see "delta" must equal the error exponentially expressed you mentioned before. Could that, say, be made equal to ZERO,
or at least further out than it is now? This clock needs whatever ratio that gives the smallest error possible- I'll add as many gears 
as needed to get that zero error. If it takes 20 gears, so be it. This is to help with an exceptionally precise astronomical clock. 
More gears will be used if needed- error is being thought of in long term- 100 years and beyond cumulative.

3. Obviously we are specifying the gear tooth numbers, and then terminal calculates the results of their combination in different orders. 
Could this be done without numbers specified, and the computer finds the lowest number of gear teeth to achieve it as variables 
w,x,y,& z (and so on)? I'm sure if the answer is yes, I'm looking at LOOOOOONG calculation times.

Confusion:

It is enabled to run as an executable, which I have done with other things before. This however is not running. I tried
running in terminal, nothing happens. Run does nothing too. Display brings up the text to edit. I can't seem to do anything
to run it.

Why are the wheel & pinion numbers defined as 3 different things? Once in pink, again a different number in blue, and near the end as its value +1.

What are the purposes of the values endw and endp (end wheel and end pinion)?

Aside from those, I don't think I understand how it works. I know the values must be constraints, but it's hard to visualize. 
And yes, I do have a decent math background (integral/differential engineering calculus, as a non-engineer, but an A- 5 years ago...)

---

### Post by oldfred on 2010-06-12
Once you make it executeable you have to use python to run it. Change to what ever directory you saved it to and this will work.

fred@fred-desktop:~$ python clockgear.py

1. From a calculation stand point there is no difference between your formula and mine.
2. The logic needs to change as right now it is hard coded with 2 wheels and pinions. I could make it 3 or 4 but as you add it becomes very unwieldy. Possibly a recursive subroutine.
3. I am just using the error to limit the number I print when I first ran it it tried to print 100*100*100*100 and scrolled by very fast. You still have to review the list to see what is best.
4. I have start and end points. I only created one end point for wheels and one for pinions. It runs from start to end of each . I originally had 1 to 100 of each and it was taking too long to calculate just for a test to see if it even worked.

My editor does not give same colors, so I am not sure of question. I have to reset start of each inner loop when I increment the outer loop. There are no constraints like it probably should have with a linear programing set of logic, just a brute force try every alternative from a start number to a end number for every gear.

There is no way with a brute force approach like this to do your desire for up to 20 gear sets.

---

### Post by BastardNamban on 2010-06-12
I'm still having trouble. I have python installed. I even set the program to open with the python executable under /bin. 
Nothing happens when I hit run, or run in terminal. Nothing launches, and system monitor confirms this- nothing new shows up. 
It just does nothing.

So I opened terminal and tried these things: ```
shogun@shadow:~$ shogun@shogun-desktop:~$ python clockgear.py
shogun@shogun-desktop:~$: command not found
shogun@shadow:~$ python clockgear.py
python: can't open file 'clockgear.py': [Errno 2] No such file or directory
shogun@shadow:~$ /home/shogun/Desktop/clockgear.py
/home/shogun/Desktop/clockgear.py: line 1: Target_gear_range: command not found
/home/shogun/Desktop/clockgear.py: line 3: w1: command not found
/home/shogun/Desktop/clockgear.py: line 4: w2: command not found
/home/shogun/Desktop/clockgear.py: line 5: endw: command not found
/home/shogun/Desktop/clockgear.py: line 7: p1: command not found
/home/shogun/Desktop/clockgear.py: line 8: p2: command not found
/home/shogun/Desktop/clockgear.py: line 9: endp: command not found
/home/shogun/Desktop/clockgear.py: line 14: wheel1: command not found
/home/shogun/Desktop/clockgear.py: line 15: syntax error near unexpected token `:'
/home/shogun/Desktop/clockgear.py: line 15: `while (wheel1 < endw):'
shogun@shadow:~$ ^C
shogun@shadow:~$ 
```

Still, nothing happens. The colors I mentioned for numbers show up when I hit display, and it opens the file as text in gedit. 

"1. From a calculation stand point there is no difference between your formula and mine."
I thought so. This shows you I do understand the ordering of the command.

"2. The logic needs to change as right now it is hard coded with 2 wheels and pinions. I could make it 3 or 4 but as you add 
it becomes very unwieldy. Possibly a recursive subroutine."

-Would 4 sets of wheels and pinons be doable? What does unwieldly mean here in context for calculation? It's possible it can crash?

"3. I am just using the error to limit the number I print when I first ran it it tried to print 100*100*100*100 and scrolled by very fast. 
You still have to review the list to see what is best."

-Does this mean 100 entry results appeared for you?

"4. I have start and end points. I only created one end point for wheels and one for pinions. It runs from start to end of each. 
I originally had 1 to 100 of each and it was taking too long to calculate just for a test to see if it even worked."

-Start points for gears? Confused. Meaning you tested tooth values from a base number of teeth for each ranging for 50 above and 50 below?

I really, really want to understand this, but I do admit my confusion- it's probably because I am not as familiar with the parsing terminology 
or conventions for writing such a script in mathematical logic as it's a new world for me. Would it be correct to say here that a mathematical 
logic circuit exists, and I'm confused as to how this logic is defined?

What I really can't figure out is why this program won't open for me, even though I've made non-executable files executable before, and with success.

I must sound like a computing greenhorn- which I'm not- but to this area of computing and, I guess, "logic"- I am.

---

### Post by oldfred on 2010-06-12
Where did you save clockgear.py? to run it you need to be in the same directory.
I copied it to ~ or /home/fred
 I do a ls to see that it really is there.
then I run it with python
fred@fred-desktop:~$ ls clo*
clockgear.py
fred@fred-desktop:~$ python clockgear.py
1.00273768044 2.19561971271e-07 51.0 79.0 49.0 82.0
etc...

I can modify for 4 if you want but it has so many while's nested it becomes hard to follow. To test for 4 I would need an answer that works so I can limit choice and see that it at least works for that.

I arbitrarily set start calc at 48 on wheels and 45 on pinions and ends at 80& 85. You can change to anything, but when running from 1 to 100 for all and before I had the logic to limit output it was listing every alternative ie 1,1,1,1 then 1,1,1,2 etc until it gets to 100,100,100,100. or 100000000 listings. I had to stop it since it was too long. Even with the logic to only show very small errors the process was slow and since I was just testing I changed starts and ends to calculate fewer alternatives. currently it starts at 48,48,45,45 and goes to 80,80,85,85.

What are reasonable start & end points. what is smallest reasonable and largest number of teeth.

---

### Post by BastardNamban on 2010-06-12
> **oldfred said:**
> Where did you save clockgear.py? to run it you need to be in the same directory.
I copied it to ~ or /home/fred
 I do a ls to see that it really is there.
then I run it with python
fred@fred-desktop:~$ ls clo*
clockgear.py
fred@fred-desktop:~$ python clockgear.py


Ok, that's where I lost you. I know how to navigate to a folder in nautilus, as that's basic use. I navigated to my desktop folder in nautilus, and clicked the clockgear.py file, but nothing happened. I assume you mean somehow to navigate to the directory in terminal? I don't know how.
I always have "shogun@shadow:~$" in terminal- aka, me@mycomputername. I don't know how to change that, or know what "ls" or " ls clo*" is.

For a 4 wheel, 4 pinion system test, try this (Wheel1/Pinion1), etc:
```
[(21/15) * (65/47) * (75/89) * (120/112)] = 1.748147263
```

What is most important to me is the final ratio of 1.002737909350795, but if there were a way to find out 
the minimum number of gears to get this number, I would be interested in that too.

---

### Post by oldfred on 2010-06-13
Did you try typing the commands just as I posted. The ls command lists files, by using clock* I list all files starting with clock so I know the file is in the directory I am in.

```
ls clock*
python clockgear.py
```

I have modified the 2 gear version, mostly to clean it up. And I will create a 4 gear version to see if it works. Rather than starting at 1 and going to 100 adn if 100 the largest possible?, is it better to start at 50 for wheels and go up, and 50 for pinions and go down to the smallest number to teeth you can have. I know you cannot have 1 tooth, but what is the smallest reasonable number?

If you will confirm the 50 as a start point I will repost the 2 gear version and start on a 4 gear set version.

---

### Post by BastardNamban on 2010-06-13
Ok, 50 for pinions and going down is a good idea. While people have made clocks with pinions of 3 leaves, 5 is a good lowend end number.

36 and up to 120 for wheels would work. The possibility of using the least number of teeth is a good thing- the less teeth, the better they can react to dust getting in them, and the stronger the individual teeth can be.

I understand what "ls clock*" is now- ls is a search function, but what doesn't seem clear to me is how you set a directory to look in. I get this just typing it into terminal: ```
shogun@shadow:~$ ls clock*
ls: cannot access clock*: No such file or directory

```

So I thought, copy the file destination into terminal with ctrl+L to get rid of the breadcrumbs layout and show file path. 
THEN maybe running ls clock* would do something. ```
bash: /home/shogun/Desktop: is a directory
shogun@shadow:~$ ls clock*
ls: cannot access clock*: No such file or directory

```
No go :(

I can't believe it's this difficult to simply run a file. Why can't I click on the file, on my desktop, to run it? Why does that refuse to do anything??

This is very frustrating, but I will be patient as you have been patient with me, and I really appreciate your help a lot.

---

### Post by oldfred on 2010-06-13
When you downloaded the file it probably is in downloads. One of my modifications is to tell the system it is python, but I think it then only runs in the background and you do not see the results in the terminal.

I use cd to change to the Downloads directory and of course I mistyped (capital D) it the first time.:p

fred@fred-desktop:~$ cd downloads
bash: cd: downloads: No such file or directory
fred@fred-desktop:~$ cd Downloads
fred@fred-desktop:~/Downloads$ ls cloc*
clockgear.py
fred@fred-desktop:~/Downloads$ python  clockgear.py
data:  (1.0027376804380288, 2.1956197127082078e-07, 51.0, 79.0, 49.0, 82.0)

---

### Post by BastardNamban on 2010-06-13
THAT'S IT! That's what I didn't know- and you just showed me. "cd"! That's why I was having so much trouble- 
to you, it was basic knowledge, but I hadn't known about it yet. I don't know basic terminal commands much yet beyond "sudo", 
but everything else I have good command over. As you can tell, I don't use the terminal alot, or compile things.

I still don't know why the thing wouldn't run by clicking on it (btw, I have downloads saved to my desktop, I forget to 
look in the downloads folder- desktop is just easier to remember, as it's right in front of me. I know, I know, it slows things down.

So, success! Here's what happened: ```
shogun@shadow:~$ cd Desktop
shogun@shadow:~/Desktop$ ls cloc*
clockgear.py
shogun@shadow:~/Desktop$ python clockgear.py
1.00273768044 2.19561971271e-07 51.0 79.0 49.0 82.0
1.00273768044 2.19561971271e-07 51.0 79.0 82.0 49.0
1.00273972603 1.82602739729e-06 54.0 61.0 45.0 73.0
1.00273972603 1.82602739729e-06 54.0 61.0 73.0 45.0
1.00273972603 1.82602739729e-06 60.0 61.0 50.0 73.0
1.00273972603 1.82602739729e-06 60.0 61.0 73.0 50.0
1.00273972603 1.82602739729e-06 61.0 54.0 45.0 73.0
1.00273972603 1.82602739729e-06 61.0 54.0 73.0 45.0
1.00273972603 1.82602739729e-06 61.0 60.0 50.0 73.0
1.00273972603 1.82602739729e-06 61.0 60.0 73.0 50.0
1.00273972603 1.82602739729e-06 61.0 66.0 55.0 73.0
1.00273972603 1.82602739729e-06 61.0 66.0 73.0 55.0
1.00273972603 1.82602739729e-06 61.0 72.0 60.0 73.0
1.00273972603 1.82602739729e-06 61.0 72.0 73.0 60.0
1.00273972603 1.82602739729e-06 61.0 78.0 65.0 73.0
1.00273972603 1.82602739729e-06 61.0 78.0 73.0 65.0
1.00273972603 1.82602739729e-06 66.0 61.0 55.0 73.0
1.00273972603 1.82602739729e-06 66.0 61.0 73.0 55.0
1.00273972603 1.82602739729e-06 72.0 61.0 60.0 73.0
1.00273972603 1.82602739729e-06 72.0 61.0 73.0 60.0
1.00273972603 1.82602739729e-06 78.0 61.0 65.0 73.0
1.00273972603 1.82602739729e-06 78.0 61.0 73.0 65.0
1.00273768044 2.19561971271e-07 79.0 51.0 49.0 82.0
1.00273768044 2.19561971271e-07 79.0 51.0 82.0 49.0
done
shogun@shadow:~/Desktop$ 

```

So, thanks to you, I now know how to navigate to a directory in terminal, and search for files in that directory, 
as well as finally successfully running your program! :p

Fred, thank you very much. I will now work on understanding the syntax of how the program defines things. Is there a 
good place to learn about what things python can do, and where to look to learn how to make such things myself? I'd like 
to be able to help others like me who don't know much yet, as some things can only be done through light coding. 

The problem for me in learning anything involved for linux has always been what I call the "robot call-center approach" 
the linux community takes toward learning online- everything is a jump through hoops wiki-list of how tos, many unintuitive, 
and often have me jumping to many separate sites before I can make use of info from one. Everything is a "read this FAQ before doing X" 
where X is any basic thing that someone could have just typed- like "use cd and then the name of a folder to change directory in terminal".

Thus, it's been quite frustrating to me to learn- if I could talk to someone in person, I pick up new stuff at a very quick pace.

I'll be waiting eagerly for your updated scripts, and once I figure out how you ordered them and the syntax, I'll try making some
of my own, but one step at a time :)

---

### Post by BastardNamban on 2010-06-13
I'm on a roll- I tried editing your file to one of my own, changed the equation order to make reading 
the resulting gear order easier (wheel1 pinion1 wheel2 pinion2 instead of wheel1 wheel2 pinion1 pinion2),
changed what I figured out to be the starting ranges for each, and saved it as a different filename. 

I also figured out it doesn't matter where you put that * at the end of something to search- the further you 
know the name of something, the further out you can make the name before you add the * to search. Interesting.

Here's what I got: ```
shogun@shadow:~/Desktop$ ls clockgear-*
clockgear-shogun.py
shogun@shadow:~/Desktop$ python clockgear-shogun.py
1.00273972603 1.82602739729e-06 36.0 61.0 30.0 73.0
1.00273972603 1.82602739729e-06 36.0 61.0 73.0 30.0
1.00273972603 1.82602739729e-06 42.0 61.0 35.0 73.0
1.00273972603 1.82602739729e-06 42.0 61.0 73.0 35.0
1.00273972603 1.82602739729e-06 48.0 61.0 40.0 73.0
1.00273972603 1.82602739729e-06 48.0 61.0 73.0 40.0
1.00273768044 2.19561971271e-07 51.0 79.0 49.0 82.0
1.00273768044 2.19561971271e-07 51.0 79.0 82.0 49.0
1.00273972603 1.82602739729e-06 54.0 61.0 45.0 73.0
1.00273972603 1.82602739729e-06 54.0 61.0 73.0 45.0
1.00273972603 1.82602739729e-06 60.0 61.0 50.0 73.0
1.00273972603 1.82602739729e-06 60.0 61.0 73.0 50.0
1.00273972603 1.82602739729e-06 61.0 36.0 30.0 73.0
1.00273972603 1.82602739729e-06 61.0 36.0 73.0 30.0
1.00273972603 1.82602739729e-06 61.0 42.0 35.0 73.0
1.00273972603 1.82602739729e-06 61.0 42.0 73.0 35.0
1.00273972603 1.82602739729e-06 61.0 48.0 40.0 73.0
1.00273972603 1.82602739729e-06 61.0 48.0 73.0 40.0
1.00273972603 1.82602739729e-06 61.0 54.0 45.0 73.0
1.00273972603 1.82602739729e-06 61.0 54.0 73.0 45.0
1.00273972603 1.82602739729e-06 61.0 60.0 50.0 73.0
1.00273972603 1.82602739729e-06 61.0 60.0 73.0 50.0
1.00273972603 1.82602739729e-06 61.0 66.0 55.0 73.0
1.00273972603 1.82602739729e-06 61.0 66.0 73.0 55.0
1.00273972603 1.82602739729e-06 61.0 72.0 60.0 73.0
1.00273972603 1.82602739729e-06 61.0 72.0 73.0 60.0
1.00273972603 1.82602739729e-06 61.0 78.0 65.0 73.0
1.00273972603 1.82602739729e-06 61.0 78.0 73.0 65.0
1.00273972603 1.82602739729e-06 66.0 61.0 55.0 73.0
1.00273972603 1.82602739729e-06 66.0 61.0 73.0 55.0
1.00273972603 1.82602739729e-06 72.0 61.0 60.0 73.0
1.00273972603 1.82602739729e-06 72.0 61.0 73.0 60.0
1.00273972603 1.82602739729e-06 78.0 61.0 65.0 73.0
1.00273972603 1.82602739729e-06 78.0 61.0 73.0 65.0
1.00273768044 2.19561971271e-07 79.0 51.0 49.0 82.0
1.00273768044 2.19561971271e-07 79.0 51.0 82.0 49.0
done
shogun@shadow:~/Desktop$ 
```

The modification I made is attached, so you can see what I did. I can even change the target number to something closer 
to the real value if I want- the wiki on Sidereal time shows me far out past the decimal, the value isn't constant- 
tidal friction actually changes the rotational speed of the earth in relation to the stars over centuries! 

This is quite amazing. My design will have to account for these sorts of minor fluctuations. I could perhaps mount this
train of gears on a differential gear series that would adjust the angular rotation of the system to account for fluxing
changes to the ratio over centuries, or something like that.

---

### Post by oldfred on 2010-06-13
Good progress.

I have a updated version. I now sort adn the default sort was in decending order. I had to increase pinion numbers to get your answer. And made the error allowed to print a variable at the top to make it easier to change to get more or less results. With only 50 descending I go no results.

Do you want me to add another set for 3 or 4? This one took about 45 seconds to calculate on my system. I think it will take a lot longer unless you restrict the start & ends.

If you know where file is and can type directory correctly,
$ python /Downloads/clockgear.py
Up arrow will let you rerun a command also
history shows all the commands you have run.

Updated & renamed to clockgear2.py jun 20, 2010

---

### Post by BastardNamban on 2010-06-14
Tried the new improved version, which I saved as "clockgearrevised" in a folder on my desktop called Clockgear, with the original and my edit of that. 
Here's what I got (took about 1 minute): ```
shogun@shadow:~$ cd Desktop/Clockgear
shogun@shadow:~/Desktop/Clockgear$ ls clock*
clockgearoriginal.py  clockgearrevised.py  clockgear-shogun.py
shogun@shadow:~/Desktop/Clockgear$ python clockgearrevised.py
data:  (1.0027376804380288, 2.1956197127082078e-07, 51.0, 79.0, 49.0, 82.0)
data:  (1.0027376804380288, 2.1956197127082078e-07, 51.0, 79.0, 82.0, 49.0)
data:  (1.0027376804380288, 2.1956197127082078e-07, 79.0, 51.0, 49.0, 82.0)
data:  (1.0027376804380288, 2.1956197127082078e-07, 79.0, 51.0, 82.0, 49.0)
done
shogun@shadow:~/Desktop/Clockgear$
```

I'm guessing I got only 4 answers, all with the same target result, with the same 4 numbers for the wheels and pinions except switched around,
because those were the most accurate answers, and less than the error value you assigned, so it posted only those 4 results.

Since that only took 1 minute to finish, I'd be willing to try up to, say, 8 gears and pinions, and let it run for a day. Really, the calculation time doesn't 
bother me much. I'm fine with letting it run for a day or a few days if I get more accurate results with wheels and pinions. 

For now, would you be able to try a version with 4 wheels and 4 pinions, and see what happens? 
I'll try 8 or 10 or 20 later on. I also think I understand completely how the code works and limits now. 

Btw, How does it know to move up or down the values though- it realizes automatically which direction to go based on which number is higher to start?

This is quite fun Fred :D

---

### Post by oldfred on 2010-06-14
You must not have as powerful processor. Mine took 8 sec and I have a new version that only takes 4 seconds.

I am working on a three gearset version and I kept stopping it after 10 minutes as I figured I must have made an infinite loops. I started to print the first wheel and each was taking about 40 seconds but I was processing wheels from 50 to 120. I came to realize I do not need to have to duplicates and a way. 
From the 2 set version
40 , 40 and every pinion 
40,41 and every pinion
I do not need to calculate 41,40 and every pinion as that is the same as the second choice. So I have changed to start the second loop of wheels at 41, 41 and so forth and same for pinions.

Near the end of the logic you see
pinion2 = pinion2 - 1
or 
wheel2 = wheel2 + 1

Each where and continue is nested at the same level and the pinions & gears are incremented or decremented.

Updated version in previous posts:

---

### Post by oldfred on 2010-06-14
This is a 3 gear set version. This includes the logic to reduce the calculation of duplicates, so each look takes less time.

On my computer with a 40-90 and 85-25 range I processed 835,822,000 combinations and found 281 within the error range I gave. It took 1052 sec or about 17.5 min.

I have no idea if it is working correctly or not. Or even if it calculated all the alternatives. I think I have an old probability book somewhere that should give me the formula for combinations and permutations , but I have not used that math for years.

Updated version Jun 16 2010 Jun20 2nd update

---

### Post by BastardNamban on 2010-06-14
Fred, I have a Dell Inspiron 9300 with a Pentium M 2.00 GHz processor.
Hardly slow, but not super fast anymore. I plan on keeping this thing as
long as possible since it cost me around $2400 new in fall of 2005.

I created a modified version of your first revised clockgear program, this:
```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
#Clockgear.py

Target_gear_range = 1.002737909350795
error_limit = .0000000001
#wheels starting & ending numbers
w1 = 5.
w2 = 5.
endw =360.
#pinions starting and ending numbers
p1 = 359.
p2 = 359.
endp = 5.

data = []

wheel1 = w1
while (wheel1 < endw):
    wheel2 = w2
    pinion1 = p1
    pinion2 = p2
    while (wheel2 < endw):
        pinion1 = p1
        pinion2 = p2
        while (pinion1 > endp):
            pinion2 = p2
            while (pinion2 > endp):
                calc_ratio = (wheel1 * wheel2 ) / (pinion1 * pinion2)
                #print calc_ratio, wheel1, wheel2, pinion1, pinion2
                #Calculated delta difference from target & current calc
                delta = abs(calc_ratio -Target_gear_range)
                if delta < error_limit:
                    data.append((calc_ratio, delta, wheel1, wheel2, pinion1, pinion2))
                pinion2 = pinion2 - 1
                continue
            pinion1 = pinion1 - 1
            continue
        wheel2 = wheel2 + 1
        continue
    wheel1 = wheel1 + 1
    continue

data.sort()
for line in data:
    print "data: ", line
    pass  
print "done"
 
```

I extended to the furthest known value, reduced the error tolerance, and upped the gear tooth range- 
this is still running as we speak, and started around 1:55 am this morning. I have no idea when it will finish.

I will try your newer-er version, and see what happens. I can't wait to see your 3 gear version- I was thinking 
if I didn't have to keep it even, we could try 5 (wheel-pinion-wheel-pinion-wheel), and keep going. 

Once you figure out the most efficient calculation parameters, let me know- from there, I can scale it up to 
as many wheels and pinions as I'd like.

I realize this may take a lot of time, but that's fine- to me, the math matters. My goal is no matter how many gears 
it takes, what combination of wheels and pinions in the smallest number will give me the most accurate result- that number 
above is a baseline ratio from the year 2000 that is the most accurate value known yet.

I really plan on making my clock so accurate that I'll have to compensate in it's design for minuscule changes over centuries, 
like tidal friction effects.

---

### Post by BastardNamban on 2010-06-14
Fred, I ran your 2nd improved clockgear.py, the one you just posted for 4 gears. It took about 7 seconds to finish with one result line on my computer. So I kicked it up a notch.

I ended the older version that had been running all day and not finished. I modified your new program again, to the furthest known value of solar to sidereal time again, and upped the tooth counts. 

I used these values, close to before: ```
Target_gear_range = 1.002737909350795
error_limit = .0000003
#wheels starting & ending numbers
w1 = 15.
endw = 360.
#pinions starting and ending numbers
p1 = 120.
endp = 5.
```

And here's what I got: ```
shogun@shadow:~/Desktop/Clockgear$ python clockgearrevised2-shogun.py
data w1,w2,p1,p2:  (1.0027376569432644, 2.5240753065425281e-07, 47.0, 226.0, 107.0, 99.0)
data w1,w2,p1,p2:  (1.0027376569432644, 2.5240753065425281e-07, 94.0, 113.0, 107.0, 99.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 17.0, 237.0, 82.0, 49.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 17.0, 237.0, 98.0, 41.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 34.0, 237.0, 98.0, 82.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 51.0, 79.0, 82.0, 49.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 51.0, 79.0, 98.0, 41.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 51.0, 158.0, 98.0, 82.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 79.0, 102.0, 98.0, 82.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 30.0, 354.0, 119.0, 89.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 36.0, 295.0, 119.0, 89.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 45.0, 236.0, 119.0, 89.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 60.0, 177.0, 119.0, 89.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 90.0, 118.0, 119.0, 89.0)
data w1,w2,p1,p2:  (1.002738173921254, 2.6457045887440245e-07, 59.0, 180.0, 119.0, 89.0)
Calculation took 673.527414 seconds
Total Count = 398098950
Delta Count = 15

done

```

With such a large gear range, this time your program finished in only about 11 minutes 22 seconds! Impressive improvements you made.

---

### Post by oldfred on 2010-06-14
i assume you can calculate that the results given are correct. With the speed up I think I do not miss any alternatives but the only way I could be sure to to review all possibilities. 

I can start on a 4 gear set (8 gears total) if you want.  I do not think I can go much further with this logic. And I have not figured out anything better. Each set seems to be an exponential increase in time. ( That was why I had to try to reduce possibilities.)

---

### Post by oldfred on 2010-06-14
I updated the clockgear3.py above that has 6 gears. I forgot to change a 2 to 3 so it wrote one of the same gears twice in the output.

I edited the file to have 4 sets. Not sure how to test. It does run.

---

### Post by BastardNamban on 2010-06-15
Fred, ran your final incarnation of the 4 gear (2 wheel, 2 pinion) clockgear on the maximum settings. 
```
Target_gear_range = 1.002737909350795
error_limit = .0000003
#wheels starting & ending numbers
w1 = 5.
endw = 360.
#pinions starting and ending numbers
p1 = 360.
endp = 5.
```
I found out how you can redirect terminal output to a text file using the "> textname.txt" output redirecting command notation. 
I had ran the file without knowing how to do that, and the output filled terminal where much of it was overwritten. So now I know 
how to redirect terminal output to text- very useful!

I added hours/minutes/seconds time at the end myself, using a calculator to divide by 60 twice- here's what I got:

```
data w1,w2,p1,p2:  (1.0027376274840778, 2.8186671729990564e-07, 258.0, 274.0, 319.0, 221.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 45.0, 350.0, 139.0, 113.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 50.0, 315.0, 139.0, 113.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 63.0, 250.0, 139.0, 113.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 70.0, 225.0, 139.0, 113.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 75.0, 210.0, 139.0, 113.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 90.0, 175.0, 139.0, 113.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 90.0, 350.0, 226.0, 139.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 90.0, 350.0, 278.0, 113.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 100.0, 315.0, 278.0, 113.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 105.0, 150.0, 139.0, 113.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 105.0, 300.0, 226.0, 139.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 105.0, 300.0, 278.0, 113.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 125.0, 126.0, 139.0, 113.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 125.0, 252.0, 226.0, 139.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 125.0, 252.0, 278.0, 113.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 126.0, 250.0, 226.0, 139.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 126.0, 250.0, 278.0, 113.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 135.0, 350.0, 339.0, 139.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 140.0, 225.0, 226.0, 139.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 140.0, 225.0, 278.0, 113.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 150.0, 210.0, 226.0, 139.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 150.0, 210.0, 278.0, 113.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 175.0, 180.0, 226.0, 139.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 175.0, 180.0, 278.0, 113.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 175.0, 270.0, 339.0, 139.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 180.0, 350.0, 278.0, 226.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 189.0, 250.0, 339.0, 139.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 200.0, 315.0, 278.0, 226.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 210.0, 225.0, 339.0, 139.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 210.0, 300.0, 278.0, 226.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 225.0, 280.0, 278.0, 226.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 250.0, 252.0, 278.0, 226.0)
data w1,w2,p1,p2:  (1.0027376329025275, 2.7644826761097363e-07, 270.0, 350.0, 339.0, 278.0)
data w1,w2,p1,p2:  (1.0027376329025277, 2.7644826738892903e-07, 100.0, 315.0, 226.0, 139.0)
data w1,w2,p1,p2:  (1.0027376329025277, 2.7644826738892903e-07, 150.0, 315.0, 339.0, 139.0)
data w1,w2,p1,p2:  (1.0027376329025277, 2.7644826738892903e-07, 300.0, 315.0, 339.0, 278.0)
data w1,w2,p1,p2:  (1.0027376401218169, 2.6922897822245773e-07, 239.0, 259.0, 253.0, 244.0)
data w1,w2,p1,p2:  (1.0027376425855512, 2.6676524389479539e-07, 19.0, 347.0, 263.0, 25.0)
data w1,w2,p1,p2:  (1.0027376425855512, 2.6676524389479539e-07, 38.0, 347.0, 263.0, 50.0)
data w1,w2,p1,p2:  (1.0027376425855512, 2.6676524389479539e-07, 76.0, 347.0, 263.0, 100.0)
data w1,w2,p1,p2:  (1.0027376425855512, 2.6676524389479539e-07, 95.0, 347.0, 263.0, 125.0)
data w1,w2,p1,p2:  (1.0027376425855512, 2.6676524389479539e-07, 152.0, 347.0, 263.0, 200.0)
data w1,w2,p1,p2:  (1.0027376425855512, 2.6676524389479539e-07, 171.0, 347.0, 263.0, 225.0)
data w1,w2,p1,p2:  (1.0027376425855512, 2.6676524389479539e-07, 190.0, 347.0, 263.0, 250.0)
data w1,w2,p1,p2:  (1.0027376425855514, 2.6676524367275078e-07, 57.0, 347.0, 263.0, 75.0)
data w1,w2,p1,p2:  (1.0027376425855514, 2.6676524367275078e-07, 114.0, 347.0, 263.0, 150.0)
data w1,w2,p1,p2:  (1.0027376425855514, 2.6676524367275078e-07, 133.0, 347.0, 263.0, 175.0)
data w1,w2,p1,p2:  (1.0027376425855514, 2.6676524367275078e-07, 209.0, 347.0, 275.0, 263.0)
data w1,w2,p1,p2:  (1.0027376425855514, 2.6676524367275078e-07, 228.0, 347.0, 300.0, 263.0)
data w1,w2,p1,p2:  (1.0027376425855514, 2.6676524367275078e-07, 247.0, 347.0, 325.0, 263.0)
data w1,w2,p1,p2:  (1.0027376425855514, 2.6676524367275078e-07, 266.0, 347.0, 350.0, 263.0)
data w1,w2,p1,p2:  (1.0027376476020844, 2.6174871070594463e-07, 101.0, 301.0, 186.0, 163.0)
data w1,w2,p1,p2:  (1.0027376476020844, 2.6174871070594463e-07, 101.0, 301.0, 326.0, 93.0)
data w1,w2,p1,p2:  (1.0027376476020844, 2.6174871070594463e-07, 202.0, 301.0, 326.0, 186.0)
data w1,w2,p1,p2:  (1.0027376476020844, 2.6174871070594463e-07, 301.0, 303.0, 326.0, 279.0)
data w1,w2,p1,p2:  (1.0027376514445479, 2.5790624724741917e-07, 55.0, 313.0, 148.0, 116.0)
data w1,w2,p1,p2:  (1.0027376514445479, 2.5790624724741917e-07, 55.0, 313.0, 296.0, 58.0)
data w1,w2,p1,p2:  (1.0027376514445479, 2.5790624724741917e-07, 110.0, 313.0, 296.0, 116.0)
data w1,w2,p1,p2:  (1.0027376514445479, 2.5790624724741917e-07, 165.0, 313.0, 232.0, 222.0)
data w1,w2,p1,p2:  (1.0027376514445479, 2.5790624724741917e-07, 220.0, 313.0, 296.0, 232.0)
data w1,w2,p1,p2:  (1.0027376514445481, 2.5790624702537457e-07, 55.0, 313.0, 232.0, 74.0)
data w1,w2,p1,p2:  (1.0027376514445481, 2.5790624702537457e-07, 110.0, 313.0, 232.0, 148.0)
data w1,w2,p1,p2:  (1.0027376514445481, 2.5790624702537457e-07, 165.0, 313.0, 296.0, 174.0)
data w1,w2,p1,p2:  (1.0027376514445481, 2.5790624702537457e-07, 165.0, 313.0, 348.0, 148.0)
data w1,w2,p1,p2:  (1.0027376514445481, 2.5790624702537457e-07, 275.0, 313.0, 296.0, 290.0)
data w1,w2,p1,p2:  (1.0027376514445481, 2.5790624702537457e-07, 313.0, 330.0, 348.0, 296.0)
data w1,w2,p1,p2:  (1.0027376569432644, 2.5240753065425281e-07, 47.0, 226.0, 107.0, 99.0)
data w1,w2,p1,p2:  (1.0027376569432644, 2.5240753065425281e-07, 47.0, 226.0, 321.0, 33.0)
data w1,w2,p1,p2:  (1.0027376569432644, 2.5240753065425281e-07, 94.0, 113.0, 107.0, 99.0)
data w1,w2,p1,p2:  (1.0027376569432644, 2.5240753065425281e-07, 94.0, 113.0, 321.0, 33.0)
data w1,w2,p1,p2:  (1.0027376569432644, 2.5240753065425281e-07, 94.0, 226.0, 198.0, 107.0)
data w1,w2,p1,p2:  (1.0027376569432644, 2.5240753065425281e-07, 94.0, 226.0, 214.0, 99.0)
data w1,w2,p1,p2:  (1.0027376569432644, 2.5240753065425281e-07, 94.0, 226.0, 321.0, 66.0)
data w1,w2,p1,p2:  (1.0027376569432644, 2.5240753065425281e-07, 94.0, 339.0, 297.0, 107.0)
data w1,w2,p1,p2:  (1.0027376569432644, 2.5240753065425281e-07, 94.0, 339.0, 321.0, 99.0)
data w1,w2,p1,p2:  (1.0027376569432644, 2.5240753065425281e-07, 113.0, 188.0, 198.0, 107.0)
data w1,w2,p1,p2:  (1.0027376569432644, 2.5240753065425281e-07, 113.0, 188.0, 214.0, 99.0)
data w1,w2,p1,p2:  (1.0027376569432644, 2.5240753065425281e-07, 113.0, 188.0, 321.0, 66.0)
data w1,w2,p1,p2:  (1.0027376569432644, 2.5240753065425281e-07, 113.0, 282.0, 297.0, 107.0)
data w1,w2,p1,p2:  (1.0027376569432644, 2.5240753065425281e-07, 113.0, 282.0, 321.0, 99.0)
data w1,w2,p1,p2:  (1.0027376569432644, 2.5240753065425281e-07, 141.0, 226.0, 297.0, 107.0)
data w1,w2,p1,p2:  (1.0027376569432644, 2.5240753065425281e-07, 141.0, 226.0, 321.0, 99.0)
data w1,w2,p1,p2:  (1.0027376569432644, 2.5240753065425281e-07, 188.0, 226.0, 214.0, 198.0)
data w1,w2,p1,p2:  (1.0027376569432644, 2.5240753065425281e-07, 188.0, 226.0, 321.0, 132.0)
data w1,w2,p1,p2:  (1.0027376569432644, 2.5240753065425281e-07, 188.0, 339.0, 297.0, 214.0)
data w1,w2,p1,p2:  (1.0027376569432644, 2.5240753065425281e-07, 188.0, 339.0, 321.0, 198.0)
data w1,w2,p1,p2:  (1.0027376569432644, 2.5240753065425281e-07, 226.0, 235.0, 321.0, 165.0)
data w1,w2,p1,p2:  (1.0027376569432644, 2.5240753065425281e-07, 226.0, 282.0, 297.0, 214.0)
data w1,w2,p1,p2:  (1.0027376569432644, 2.5240753065425281e-07, 226.0, 282.0, 321.0, 198.0)
data w1,w2,p1,p2:  (1.0027376569432644, 2.5240753065425281e-07, 226.0, 329.0, 321.0, 231.0)
data w1,w2,p1,p2:  (1.0027376569432644, 2.5240753065425281e-07, 282.0, 339.0, 321.0, 297.0)
data w1,w2,p1,p2:  (1.0027376621467681, 2.4720402702627098e-07, 185.0, 295.0, 282.0, 193.0)
data w1,w2,p1,p2:  (1.0027376663167751, 2.4303402001990548e-07, 223.0, 317.0, 349.0, 202.0)
data w1,w2,p1,p2:  (1.0027376703439324, 2.3900686274558325e-07, 197.0, 251.0, 268.0, 184.0)
data w1,w2,p1,p2:  (1.0027376717583873, 2.3759240774801071e-07, 217.0, 265.0, 243.0, 236.0)
data w1,w2,p1,p2:  (1.0027376717583873, 2.3759240774801071e-07, 217.0, 265.0, 324.0, 177.0)
data w1,w2,p1,p2:  (1.0027376717583873, 2.3759240774801071e-07, 217.0, 265.0, 354.0, 162.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 17.0, 237.0, 82.0, 49.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 17.0, 237.0, 98.0, 41.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 17.0, 237.0, 287.0, 14.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 34.0, 237.0, 98.0, 82.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 34.0, 237.0, 164.0, 49.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 34.0, 237.0, 196.0, 41.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 34.0, 237.0, 287.0, 28.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 51.0, 79.0, 82.0, 49.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 51.0, 79.0, 98.0, 41.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 51.0, 158.0, 98.0, 82.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 51.0, 158.0, 164.0, 49.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 51.0, 158.0, 196.0, 41.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 51.0, 237.0, 123.0, 98.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 51.0, 237.0, 147.0, 82.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 51.0, 237.0, 246.0, 49.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 51.0, 237.0, 294.0, 41.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 51.0, 316.0, 164.0, 98.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 51.0, 316.0, 196.0, 82.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 51.0, 316.0, 328.0, 49.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 68.0, 237.0, 164.0, 98.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 68.0, 237.0, 196.0, 82.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 68.0, 237.0, 287.0, 56.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 68.0, 237.0, 328.0, 49.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 79.0, 102.0, 98.0, 82.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 79.0, 102.0, 164.0, 49.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 79.0, 102.0, 196.0, 41.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 79.0, 102.0, 287.0, 28.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 79.0, 153.0, 287.0, 42.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 79.0, 204.0, 164.0, 98.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 79.0, 204.0, 196.0, 82.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 79.0, 204.0, 287.0, 56.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 79.0, 204.0, 328.0, 49.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 79.0, 255.0, 205.0, 98.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 79.0, 255.0, 245.0, 82.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 79.0, 255.0, 287.0, 70.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 79.0, 306.0, 164.0, 147.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 79.0, 306.0, 196.0, 123.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 79.0, 306.0, 287.0, 84.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 79.0, 357.0, 287.0, 98.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 79.0, 357.0, 343.0, 82.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 85.0, 237.0, 205.0, 98.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 85.0, 237.0, 245.0, 82.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 85.0, 237.0, 287.0, 70.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 102.0, 158.0, 164.0, 98.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 102.0, 158.0, 196.0, 82.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 102.0, 158.0, 328.0, 49.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 102.0, 237.0, 164.0, 147.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 102.0, 237.0, 196.0, 123.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 102.0, 237.0, 246.0, 98.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 102.0, 237.0, 294.0, 82.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 102.0, 316.0, 196.0, 164.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 102.0, 316.0, 328.0, 98.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 119.0, 237.0, 287.0, 98.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 119.0, 237.0, 343.0, 82.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 136.0, 237.0, 196.0, 164.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 136.0, 237.0, 287.0, 112.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 136.0, 237.0, 328.0, 98.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 153.0, 158.0, 246.0, 98.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 153.0, 158.0, 287.0, 84.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 153.0, 158.0, 294.0, 82.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 153.0, 237.0, 246.0, 147.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 153.0, 237.0, 287.0, 126.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 153.0, 237.0, 294.0, 123.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 153.0, 316.0, 246.0, 196.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 153.0, 316.0, 287.0, 168.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 153.0, 316.0, 294.0, 164.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 158.0, 204.0, 196.0, 164.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 158.0, 204.0, 287.0, 112.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 158.0, 204.0, 328.0, 98.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 158.0, 255.0, 205.0, 196.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 158.0, 255.0, 245.0, 164.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 158.0, 255.0, 287.0, 140.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 158.0, 306.0, 287.0, 168.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 158.0, 306.0, 328.0, 147.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 158.0, 357.0, 287.0, 196.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 158.0, 357.0, 343.0, 164.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 170.0, 237.0, 205.0, 196.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 170.0, 237.0, 245.0, 164.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 170.0, 237.0, 287.0, 140.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 187.0, 237.0, 287.0, 154.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 204.0, 237.0, 246.0, 196.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 204.0, 237.0, 294.0, 164.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 204.0, 237.0, 328.0, 147.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 204.0, 316.0, 328.0, 196.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 221.0, 237.0, 287.0, 182.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 237.0, 238.0, 287.0, 196.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 237.0, 238.0, 343.0, 164.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 237.0, 255.0, 246.0, 245.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 237.0, 255.0, 287.0, 210.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 237.0, 255.0, 294.0, 205.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 237.0, 272.0, 287.0, 224.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 237.0, 272.0, 328.0, 196.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 237.0, 289.0, 287.0, 238.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 237.0, 306.0, 287.0, 252.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 237.0, 306.0, 294.0, 246.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 237.0, 323.0, 287.0, 266.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 237.0, 340.0, 287.0, 280.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 237.0, 340.0, 328.0, 245.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 237.0, 357.0, 294.0, 287.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 237.0, 357.0, 343.0, 246.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 255.0, 316.0, 287.0, 280.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 255.0, 316.0, 328.0, 245.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 306.0, 316.0, 336.0, 287.0)
data w1,w2,p1,p2:  (1.0027376804380288, 2.2891276629799506e-07, 316.0, 357.0, 343.0, 328.0)
data w1,w2,p1,p2:  (1.002737680438029, 2.2891276607595046e-07, 51.0, 79.0, 287.0, 14.0)
data w1,w2,p1,p2:  (1.002737680438029, 2.2891276607595046e-07, 51.0, 158.0, 287.0, 28.0)
data w1,w2,p1,p2:  (1.002737680438029, 2.2891276607595046e-07, 51.0, 237.0, 287.0, 42.0)
data w1,w2,p1,p2:  (1.002737680438029, 2.2891276607595046e-07, 51.0, 316.0, 287.0, 56.0)
data w1,w2,p1,p2:  (1.002737680438029, 2.2891276607595046e-07, 79.0, 153.0, 123.0, 98.0)
data w1,w2,p1,p2:  (1.002737680438029, 2.2891276607595046e-07, 79.0, 153.0, 147.0, 82.0)
data w1,w2,p1,p2:  (1.002737680438029, 2.2891276607595046e-07, 79.0, 153.0, 246.0, 49.0)
data w1,w2,p1,p2:  (1.002737680438029, 2.2891276607595046e-07, 79.0, 153.0, 294.0, 41.0)
data w1,w2,p1,p2:  (1.002737680438029, 2.2891276607595046e-07, 79.0, 306.0, 246.0, 98.0)
data w1,w2,p1,p2:  (1.002737680438029, 2.2891276607595046e-07, 79.0, 306.0, 294.0, 82.0)
data w1,w2,p1,p2:  (1.002737680438029, 2.2891276607595046e-07, 102.0, 158.0, 287.0, 56.0)
data w1,w2,p1,p2:  (1.002737680438029, 2.2891276607595046e-07, 102.0, 237.0, 287.0, 84.0)
data w1,w2,p1,p2:  (1.002737680438029, 2.2891276607595046e-07, 102.0, 316.0, 287.0, 112.0)
data w1,w2,p1,p2:  (1.002737680438029, 2.2891276607595046e-07, 153.0, 158.0, 164.0, 147.0)
data w1,w2,p1,p2:  (1.002737680438029, 2.2891276607595046e-07, 153.0, 158.0, 196.0, 123.0)
data w1,w2,p1,p2:  (1.002737680438029, 2.2891276607595046e-07, 153.0, 316.0, 328.0, 147.0)
data w1,w2,p1,p2:  (1.002737680438029, 2.2891276607595046e-07, 158.0, 306.0, 246.0, 196.0)
data w1,w2,p1,p2:  (1.002737680438029, 2.2891276607595046e-07, 158.0, 306.0, 294.0, 164.0)
data w1,w2,p1,p2:  (1.002737680438029, 2.2891276607595046e-07, 204.0, 237.0, 287.0, 168.0)
data w1,w2,p1,p2:  (1.002737680438029, 2.2891276607595046e-07, 204.0, 316.0, 287.0, 224.0)
data w1,w2,p1,p2:  (1.002737680438029, 2.2891276607595046e-07, 306.0, 316.0, 328.0, 294.0)
data w1,w2,p1,p2:  (1.002737698853126, 2.1049766907310641e-07, 44.0, 308.0, 255.0, 53.0)
data w1,w2,p1,p2:  (1.002737698853126, 2.1049766907310641e-07, 44.0, 308.0, 265.0, 51.0)
data w1,w2,p1,p2:  (1.002737698853126, 2.1049766907310641e-07, 56.0, 242.0, 159.0, 85.0)
data w1,w2,p1,p2:  (1.002737698853126, 2.1049766907310641e-07, 88.0, 154.0, 255.0, 53.0)
data w1,w2,p1,p2:  (1.002737698853126, 2.1049766907310641e-07, 88.0, 154.0, 265.0, 51.0)
data w1,w2,p1,p2:  (1.002737698853126, 2.1049766907310641e-07, 88.0, 308.0, 255.0, 106.0)
data w1,w2,p1,p2:  (1.002737698853126, 2.1049766907310641e-07, 88.0, 308.0, 265.0, 102.0)
data w1,w2,p1,p2:  (1.002737698853126, 2.1049766907310641e-07, 112.0, 121.0, 159.0, 85.0)
data w1,w2,p1,p2:  (1.002737698853126, 2.1049766907310641e-07, 112.0, 242.0, 318.0, 85.0)
data w1,w2,p1,p2:  (1.002737698853126, 2.1049766907310641e-07, 121.0, 224.0, 170.0, 159.0)
data w1,w2,p1,p2:  (1.002737698853126, 2.1049766907310641e-07, 121.0, 224.0, 255.0, 106.0)
data w1,w2,p1,p2:  (1.002737698853126, 2.1049766907310641e-07, 121.0, 336.0, 255.0, 159.0)
data w1,w2,p1,p2:  (1.002737698853126, 2.1049766907310641e-07, 132.0, 308.0, 265.0, 153.0)
data w1,w2,p1,p2:  (1.002737698853126, 2.1049766907310641e-07, 168.0, 242.0, 265.0, 153.0)
data w1,w2,p1,p2:  (1.002737698853126, 2.1049766907310641e-07, 176.0, 231.0, 255.0, 159.0)
data w1,w2,p1,p2:  (1.002737698853126, 2.1049766907310641e-07, 176.0, 231.0, 265.0, 153.0)
data w1,w2,p1,p2:  (1.002737698853126, 2.1049766907310641e-07, 176.0, 308.0, 255.0, 212.0)
data w1,w2,p1,p2:  (1.002737698853126, 2.1049766907310641e-07, 176.0, 308.0, 265.0, 204.0)
data w1,w2,p1,p2:  (1.002737698853126, 2.1049766907310641e-07, 224.0, 242.0, 318.0, 170.0)
data w1,w2,p1,p2:  (1.002737698853126, 2.1049766907310641e-07, 231.0, 352.0, 306.0, 265.0)
data w1,w2,p1,p2:  (1.002737698853126, 2.1049766907310641e-07, 231.0, 352.0, 318.0, 255.0)
data w1,w2,p1,p2:  (1.002737698853126, 2.1049766907310641e-07, 242.0, 336.0, 306.0, 265.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 44.0, 308.0, 159.0, 85.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 56.0, 242.0, 255.0, 53.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 56.0, 242.0, 265.0, 51.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 77.0, 176.0, 159.0, 85.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 77.0, 176.0, 255.0, 53.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 77.0, 176.0, 265.0, 51.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 77.0, 352.0, 170.0, 159.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 77.0, 352.0, 255.0, 106.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 77.0, 352.0, 265.0, 102.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 77.0, 352.0, 318.0, 85.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 88.0, 154.0, 159.0, 85.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 88.0, 308.0, 170.0, 159.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 88.0, 308.0, 318.0, 85.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 112.0, 121.0, 255.0, 53.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 112.0, 121.0, 265.0, 51.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 112.0, 242.0, 170.0, 159.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 112.0, 242.0, 255.0, 106.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 112.0, 242.0, 265.0, 102.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 121.0, 224.0, 265.0, 102.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 121.0, 224.0, 318.0, 85.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 121.0, 336.0, 265.0, 153.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 132.0, 308.0, 255.0, 159.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 154.0, 176.0, 170.0, 159.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 154.0, 176.0, 255.0, 106.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 154.0, 176.0, 265.0, 102.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 154.0, 176.0, 318.0, 85.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 154.0, 264.0, 255.0, 159.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 154.0, 264.0, 265.0, 153.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 154.0, 352.0, 255.0, 212.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 154.0, 352.0, 265.0, 204.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 154.0, 352.0, 318.0, 170.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 154.0, 352.0, 340.0, 159.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 168.0, 242.0, 255.0, 159.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 176.0, 308.0, 318.0, 170.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 176.0, 308.0, 340.0, 159.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 220.0, 308.0, 265.0, 255.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 224.0, 242.0, 255.0, 212.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 224.0, 242.0, 265.0, 204.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 224.0, 242.0, 340.0, 159.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 242.0, 280.0, 265.0, 255.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 242.0, 336.0, 318.0, 255.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 264.0, 308.0, 306.0, 265.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 264.0, 308.0, 318.0, 255.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 308.0, 308.0, 357.0, 265.0)
data w1,w2,p1,p2:  (1.0027376988531262, 2.104976688510618e-07, 308.0, 352.0, 340.0, 318.0)
data w1,w2,p1,p2:  (1.0027377277916367, 1.8155915837425596e-07, 307.0, 309.0, 353.0, 268.0)
data w1,w2,p1,p2:  (1.002737736059895, 1.7329090007400794e-07, 131.0, 137.0, 157.0, 114.0)
data w1,w2,p1,p2:  (1.002737736059895, 1.7329090007400794e-07, 131.0, 137.0, 314.0, 57.0)
data w1,w2,p1,p2:  (1.002737736059895, 1.7329090007400794e-07, 131.0, 274.0, 228.0, 157.0)
data w1,w2,p1,p2:  (1.002737736059895, 1.7329090007400794e-07, 131.0, 274.0, 314.0, 114.0)
data w1,w2,p1,p2:  (1.002737736059895, 1.7329090007400794e-07, 137.0, 262.0, 228.0, 157.0)
data w1,w2,p1,p2:  (1.002737736059895, 1.7329090007400794e-07, 137.0, 262.0, 314.0, 114.0)
data w1,w2,p1,p2:  (1.002737736059895, 1.7329090007400794e-07, 262.0, 274.0, 314.0, 228.0)
data w1,w2,p1,p2:  (1.0027377447182189, 1.6463257623833272e-07, 92.0, 211.0, 239.0, 81.0)
data w1,w2,p1,p2:  (1.0027377447182189, 1.6463257623833272e-07, 184.0, 211.0, 239.0, 162.0)
data w1,w2,p1,p2:  (1.0027377447182189, 1.6463257623833272e-07, 211.0, 276.0, 243.0, 239.0)
data w1,w2,p1,p2:  (1.0027377636291286, 1.4572166651127816e-07, 249.0, 253.0, 359.0, 175.0)
data w1,w2,p1,p2:  (1.0027377663772692, 1.4297352590730839e-07, 173.0, 235.0, 224.0, 181.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 24.0, 351.0, 271.0, 31.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 26.0, 324.0, 271.0, 31.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 27.0, 312.0, 271.0, 31.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 39.0, 216.0, 271.0, 31.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 48.0, 351.0, 271.0, 62.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 52.0, 162.0, 271.0, 31.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 52.0, 324.0, 271.0, 62.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 54.0, 156.0, 271.0, 31.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 54.0, 312.0, 271.0, 62.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 78.0, 108.0, 271.0, 31.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 78.0, 216.0, 271.0, 62.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 78.0, 324.0, 271.0, 93.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 96.0, 351.0, 271.0, 124.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 104.0, 162.0, 271.0, 62.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 104.0, 243.0, 271.0, 93.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 104.0, 324.0, 271.0, 124.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 108.0, 156.0, 271.0, 62.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 108.0, 234.0, 271.0, 93.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 108.0, 312.0, 271.0, 124.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 117.0, 144.0, 271.0, 62.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 117.0, 216.0, 271.0, 93.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 117.0, 288.0, 271.0, 124.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 130.0, 324.0, 271.0, 155.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 135.0, 312.0, 271.0, 155.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 156.0, 162.0, 271.0, 93.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 156.0, 216.0, 271.0, 124.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 156.0, 270.0, 271.0, 155.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 156.0, 324.0, 271.0, 186.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 182.0, 324.0, 271.0, 217.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 189.0, 312.0, 271.0, 217.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 192.0, 351.0, 271.0, 248.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 195.0, 216.0, 271.0, 155.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 208.0, 243.0, 271.0, 186.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 208.0, 324.0, 271.0, 248.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 216.0, 234.0, 271.0, 186.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 216.0, 273.0, 271.0, 217.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 216.0, 312.0, 271.0, 248.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 216.0, 351.0, 279.0, 271.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 234.0, 252.0, 271.0, 217.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 234.0, 288.0, 271.0, 248.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 240.0, 351.0, 310.0, 271.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 243.0, 312.0, 279.0, 271.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 264.0, 351.0, 341.0, 271.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 270.0, 312.0, 310.0, 271.0)
data w1,w2,p1,p2:  (1.0027377693131769, 1.4003761816816507e-07, 297.0, 312.0, 341.0, 271.0)
data w1,w2,p1,p2:  (1.0027377693131772, 1.4003761794612046e-07, 36.0, 234.0, 271.0, 31.0)
data w1,w2,p1,p2:  (1.0027377693131772, 1.4003761794612046e-07, 72.0, 117.0, 271.0, 31.0)
data w1,w2,p1,p2:  (1.0027377693131772, 1.4003761794612046e-07, 72.0, 234.0, 271.0, 62.0)
data w1,w2,p1,p2:  (1.0027377693131772, 1.4003761794612046e-07, 72.0, 351.0, 271.0, 93.0)
data w1,w2,p1,p2:  (1.0027377693131772, 1.4003761794612046e-07, 81.0, 104.0, 271.0, 31.0)
data w1,w2,p1,p2:  (1.0027377693131772, 1.4003761794612046e-07, 81.0, 208.0, 271.0, 62.0)
data w1,w2,p1,p2:  (1.0027377693131772, 1.4003761794612046e-07, 81.0, 312.0, 271.0, 93.0)
data w1,w2,p1,p2:  (1.0027377693131772, 1.4003761794612046e-07, 120.0, 351.0, 271.0, 155.0)
data w1,w2,p1,p2:  (1.0027377693131772, 1.4003761794612046e-07, 144.0, 234.0, 271.0, 124.0)
data w1,w2,p1,p2:  (1.0027377693131772, 1.4003761794612046e-07, 144.0, 351.0, 271.0, 186.0)
data w1,w2,p1,p2:  (1.0027377693131772, 1.4003761794612046e-07, 162.0, 208.0, 271.0, 124.0)
data w1,w2,p1,p2:  (1.0027377693131772, 1.4003761794612046e-07, 162.0, 260.0, 271.0, 155.0)
data w1,w2,p1,p2:  (1.0027377693131772, 1.4003761794612046e-07, 162.0, 312.0, 271.0, 186.0)
data w1,w2,p1,p2:  (1.0027377693131772, 1.4003761794612046e-07, 168.0, 351.0, 271.0, 217.0)
data w1,w2,p1,p2:  (1.0027377693131772, 1.4003761794612046e-07, 180.0, 234.0, 271.0, 155.0)
data w1,w2,p1,p2:  (1.0027377693131772, 1.4003761794612046e-07, 234.0, 324.0, 279.0, 271.0)
data w1,w2,p1,p2:  (1.0027377693131772, 1.4003761794612046e-07, 260.0, 324.0, 310.0, 271.0)
data w1,w2,p1,p2:  (1.0027377693131772, 1.4003761794612046e-07, 286.0, 324.0, 341.0, 271.0)
data w1,w2,p1,p2:  (1.0027377712882457, 1.3806254939296991e-07, 223.0, 271.0, 247.0, 244.0)
data w1,w2,p1,p2:  (1.0027377777777777, 1.315730173701013e-07, 118.0, 239.0, 225.0, 125.0)
data w1,w2,p1,p2:  (1.0027377777777777, 1.315730173701013e-07, 236.0, 239.0, 250.0, 225.0)
data w1,w2,p1,p2:  (1.0027377846490804, 1.2470171473211167e-07, 172.0, 181.0, 237.0, 131.0)
data w1,w2,p1,p2:  (1.0027377846490804, 1.2470171473211167e-07, 181.0, 344.0, 262.0, 237.0)
data w1,w2,p1,p2:  (1.0027377861694595, 1.231813355762057e-07, 73.0, 291.0, 223.0, 95.0)
data w1,w2,p1,p2:  (1.0027377861694595, 1.231813355762057e-07, 97.0, 219.0, 223.0, 95.0)
data w1,w2,p1,p2:  (1.0027377861694595, 1.231813355762057e-07, 146.0, 291.0, 223.0, 190.0)
data w1,w2,p1,p2:  (1.0027377861694595, 1.231813355762057e-07, 194.0, 219.0, 223.0, 190.0)
data w1,w2,p1,p2:  (1.0027377861694595, 1.231813355762057e-07, 219.0, 291.0, 285.0, 223.0)
data w1,w2,p1,p2:  (1.0027378115835777, 9.7767217432931375e-08, 287.0, 305.0, 341.0, 256.0)
data w1,w2,p1,p2:  (1.0027378115835777, 9.7767217432931375e-08, 287.0, 305.0, 352.0, 248.0)
data w1,w2,p1,p2:  (1.0027378222500174, 8.7100777701465404e-08, 232.0, 311.0, 351.0, 205.0)
data w1,w2,p1,p2:  (1.002737831858407, 7.7492388061983775e-08, 101.0, 359.0, 226.0, 160.0)
data w1,w2,p1,p2:  (1.002737831858407, 7.7492388061983775e-08, 101.0, 359.0, 320.0, 113.0)
data w1,w2,p1,p2:  (1.002737831858407, 7.7492388061983775e-08, 202.0, 359.0, 320.0, 226.0)
data w1,w2,p1,p2:  (1.002737831858407, 7.7492388061983775e-08, 303.0, 359.0, 339.0, 320.0)
data w1,w2,p1,p2:  (1.0027378637110327, 4.5639762413784979e-08, 159.0, 334.0, 251.0, 211.0)
data w1,w2,p1,p2:  (1.0027378637110327, 4.5639762413784979e-08, 167.0, 318.0, 251.0, 211.0)
data w1,w2,p1,p2:  (1.0027378739225958, 3.5428199263165538e-08, 163.0, 182.0, 305.0, 97.0)
data w1,w2,p1,p2:  (1.0027378739225958, 3.5428199263165538e-08, 273.0, 326.0, 305.0, 291.0)
data w1,w2,p1,p2:  (1.0027378739225961, 3.5428199041120934e-08, 91.0, 326.0, 305.0, 97.0)
data w1,w2,p1,p2:  (1.0027378739225961, 3.5428199041120934e-08, 182.0, 326.0, 305.0, 194.0)
data w1,w2,p1,p2:  (1.0027378836639609, 2.5686834215221666e-08, 68.0, 307.0, 191.0, 109.0)
data w1,w2,p1,p2:  (1.0027378836639609, 2.5686834215221666e-08, 136.0, 307.0, 218.0, 191.0)
data w1,w2,p1,p2:  (1.0027378836639609, 2.5686834215221666e-08, 204.0, 307.0, 327.0, 191.0)
data w1,w2,p1,p2:  (1.0027378906591324, 1.8691662662106978e-08, 173.0, 199.0, 247.0, 139.0)
data w1,w2,p1,p2:  (1.0027378906591324, 1.8691662662106978e-08, 199.0, 346.0, 278.0, 247.0)
data w1,w2,p1,p2:  (1.0027379049488028, 4.4019923262084149e-09, 180.0, 352.0, 353.0, 179.0)
data w1,w2,p1,p2:  (1.0027379049488028, 4.4019923262084149e-09, 192.0, 330.0, 353.0, 179.0)
data w1,w2,p1,p2:  (1.0027379049488028, 4.4019923262084149e-09, 198.0, 320.0, 353.0, 179.0)
data w1,w2,p1,p2:  (1.0027379049488028, 4.4019923262084149e-09, 220.0, 288.0, 353.0, 179.0)
data w1,w2,p1,p2:  (1.0027379049488028, 4.4019923262084149e-09, 240.0, 264.0, 353.0, 179.0)
data w1,w2,p1,p2:  (1.0027379053694843, 3.9813108365649441e-09, 119.0, 317.0, 198.0, 190.0)
data w1,w2,p1,p2:  (1.0027379053694843, 3.9813108365649441e-09, 119.0, 317.0, 209.0, 180.0)
data w1,w2,p1,p2:  (1.0027379053694843, 3.9813108365649441e-09, 119.0, 317.0, 220.0, 171.0)
data w1,w2,p1,p2:  (1.0027379053694843, 3.9813108365649441e-09, 119.0, 317.0, 228.0, 165.0)
data w1,w2,p1,p2:  (1.0027379053694843, 3.9813108365649441e-09, 119.0, 317.0, 285.0, 132.0)
data w1,w2,p1,p2:  (1.0027379053694843, 3.9813108365649441e-09, 119.0, 317.0, 330.0, 114.0)
data w1,w2,p1,p2:  (1.0027379053694843, 3.9813108365649441e-09, 119.0, 317.0, 342.0, 110.0)
data w1,w2,p1,p2:  (1.0027379053694843, 3.9813108365649441e-09, 238.0, 317.0, 285.0, 264.0)
data w1,w2,p1,p2:  (1.0027379053694843, 3.9813108365649441e-09, 238.0, 317.0, 330.0, 228.0)
data w1,w2,p1,p2:  (1.0027379053694843, 3.9813108365649441e-09, 238.0, 317.0, 342.0, 220.0)
data w1,w2,p1,p2:  (1.0027379053694843, 3.9813108365649441e-09, 238.0, 317.0, 360.0, 209.0)
data w1,w2,p1,p2:  (1.0027379053694843, 3.9813108365649441e-09, 317.0, 357.0, 342.0, 330.0)
data w1,w2,p1,p2:  (1.0027379154078548, 6.0570597426590211e-09, 129.0, 247.0, 331.0, 96.0)
data w1,w2,p1,p2:  (1.0027379154078551, 6.0570599647036261e-09, 43.0, 247.0, 331.0, 32.0)
data w1,w2,p1,p2:  (1.0027379154078551, 6.0570599647036261e-09, 86.0, 247.0, 331.0, 64.0)
data w1,w2,p1,p2:  (1.0027379154078551, 6.0570599647036261e-09, 172.0, 247.0, 331.0, 128.0)
data w1,w2,p1,p2:  (1.0027379154078551, 6.0570599647036261e-09, 215.0, 247.0, 331.0, 160.0)
data w1,w2,p1,p2:  (1.0027379154078551, 6.0570599647036261e-09, 247.0, 258.0, 331.0, 192.0)
data w1,w2,p1,p2:  (1.0027379154078551, 6.0570599647036261e-09, 247.0, 301.0, 331.0, 224.0)
data w1,w2,p1,p2:  (1.0027379154078551, 6.0570599647036261e-09, 247.0, 344.0, 331.0, 256.0)
data w1,w2,p1,p2:  (1.0027379191814221, 9.8306269791237355e-09, 223.0, 225.0, 254.0, 197.0)
data w1,w2,p1,p2:  (1.0027379312661673, 2.1915372183656245e-08, 201.0, 297.0, 289.0, 206.0)
data w1,w2,p1,p2:  (1.0027379337080828, 2.4357287742304834e-08, 155.0, 267.0, 268.0, 154.0)
data w1,w2,p1,p2:  (1.0027379337080828, 2.4357287742304834e-08, 267.0, 310.0, 308.0, 268.0)
data w1,w2,p1,p2:  (1.0027379337080831, 2.4357287964349439e-08, 155.0, 267.0, 308.0, 134.0)
data w1,w2,p1,p2:  (1.0027379414654609, 3.2114665815541343e-08, 253.0, 359.0, 327.0, 277.0)
data w1,w2,p1,p2:  (1.0027379451623069, 3.5811511756023151e-08, 213.0, 239.0, 334.0, 152.0)
data w1,w2,p1,p2:  (1.0027379451623071, 3.5811511978067756e-08, 213.0, 239.0, 304.0, 167.0)
data w1,w2,p1,p2:  (1.0027379664683613, 5.7117566232278705e-08, 85.0, 349.0, 172.0, 172.0)
data w1,w2,p1,p2:  (1.0027379664683613, 5.7117566232278705e-08, 85.0, 349.0, 344.0, 86.0)
data w1,w2,p1,p2:  (1.0027379664683613, 5.7117566232278705e-08, 170.0, 349.0, 344.0, 172.0)
data w1,w2,p1,p2:  (1.0027379664683613, 5.7117566232278705e-08, 255.0, 349.0, 344.0, 258.0)
data w1,w2,p1,p2:  (1.0027379664683613, 5.7117566232278705e-08, 340.0, 349.0, 344.0, 344.0)
data w1,w2,p1,p2:  (1.0027379693971268, 6.0046331684660004e-08, 163.0, 355.0, 299.0, 193.0)
data w1,w2,p1,p2:  (1.0027379815345432, 7.218374808992678e-08, 62.0, 254.0, 349.0, 45.0)
data w1,w2,p1,p2:  (1.0027379815345432, 7.218374808992678e-08, 124.0, 127.0, 349.0, 45.0)
data w1,w2,p1,p2:  (1.0027379815345432, 7.218374808992678e-08, 124.0, 254.0, 349.0, 90.0)
data w1,w2,p1,p2:  (1.0027379815345432, 7.218374808992678e-08, 127.0, 248.0, 349.0, 90.0)
data w1,w2,p1,p2:  (1.0027379815345432, 7.218374808992678e-08, 186.0, 254.0, 349.0, 135.0)
data w1,w2,p1,p2:  (1.0027379815345432, 7.218374808992678e-08, 248.0, 254.0, 349.0, 180.0)
data w1,w2,p1,p2:  (1.0027379815345432, 7.218374808992678e-08, 254.0, 310.0, 349.0, 225.0)
data w1,w2,p1,p2:  (1.0027379840132875, 7.4662492410837444e-08, 275.0, 281.0, 312.0, 247.0)
data w1,w2,p1,p2:  (1.0027379840132877, 7.4662492632882049e-08, 275.0, 281.0, 338.0, 228.0)
data w1,w2,p1,p2:  (1.0027379865878339, 7.7237038764721433e-08, 95.0, 266.0, 319.0, 79.0)
data w1,w2,p1,p2:  (1.0027379865878339, 7.7237038764721433e-08, 133.0, 190.0, 319.0, 79.0)
data w1,w2,p1,p2:  (1.0027379865878339, 7.7237038764721433e-08, 190.0, 266.0, 319.0, 158.0)
data w1,w2,p1,p2:  (1.0027379865878339, 7.7237038764721433e-08, 266.0, 285.0, 319.0, 237.0)
data w1,w2,p1,p2:  (1.0027380015735641, 9.2222768977023861e-08, 89.0, 358.0, 205.0, 155.0)
data w1,w2,p1,p2:  (1.0027380015735641, 9.2222768977023861e-08, 178.0, 179.0, 205.0, 155.0)
data w1,w2,p1,p2:  (1.0027380015735641, 9.2222768977023861e-08, 178.0, 358.0, 310.0, 205.0)
data w1,w2,p1,p2:  (1.0027380015735641, 9.2222768977023861e-08, 179.0, 356.0, 310.0, 205.0)
data w1,w2,p1,p2:  (1.0027380183870178, 1.0903622271740687e-07, 202.0, 223.0, 269.0, 167.0)
data w1,w2,p1,p2:  (1.0027380191169477, 1.0976615261171219e-07, 220.0, 278.0, 251.0, 243.0)
data w1,w2,p1,p2:  (1.0027380246704489, 1.1531965382616249e-07, 107.0, 332.0, 241.0, 147.0)
data w1,w2,p1,p2:  (1.0027380246704491, 1.153196540482071e-07, 166.0, 214.0, 241.0, 147.0)
data w1,w2,p1,p2:  (1.0027380246704491, 1.153196540482071e-07, 214.0, 332.0, 294.0, 241.0)
data w1,w2,p1,p2:  (1.0027380257009346, 1.1635013952293605e-07, 121.0, 227.0, 214.0, 128.0)
data w1,w2,p1,p2:  (1.0027380257009346, 1.1635013952293605e-07, 121.0, 227.0, 256.0, 107.0)
data w1,w2,p1,p2:  (1.0027380257009346, 1.1635013952293605e-07, 227.0, 242.0, 256.0, 214.0)
data w1,w2,p1,p2:  (1.0027380339680905, 1.2461729537172062e-07, 164.0, 297.0, 335.0, 145.0)
data w1,w2,p1,p2:  (1.0027380339680907, 1.2461729559376522e-07, 198.0, 246.0, 335.0, 145.0)
data w1,w2,p1,p2:  (1.0027380339680907, 1.2461729559376522e-07, 297.0, 328.0, 335.0, 290.0)
data w1,w2,p1,p2:  (1.0027380533920411, 1.4404124604183721e-07, 203.0, 267.0, 283.0, 191.0)
data w1,w2,p1,p2:  (1.0027380556479326, 1.4629713751546092e-07, 289.0, 313.0, 310.0, 291.0)
data w1,w2,p1,p2:  (1.0027380590203832, 1.4966958805651132e-07, 48.0, 206.0, 173.0, 57.0)
data w1,w2,p1,p2:  (1.0027380590203832, 1.4966958805651132e-07, 96.0, 103.0, 173.0, 57.0)
data w1,w2,p1,p2:  (1.0027380590203832, 1.4966958805651132e-07, 96.0, 206.0, 173.0, 114.0)
data w1,w2,p1,p2:  (1.0027380590203832, 1.4966958805651132e-07, 96.0, 206.0, 346.0, 57.0)
data w1,w2,p1,p2:  (1.0027380590203832, 1.4966958805651132e-07, 96.0, 309.0, 173.0, 171.0)
data w1,w2,p1,p2:  (1.0027380590203832, 1.4966958805651132e-07, 103.0, 128.0, 173.0, 76.0)
data w1,w2,p1,p2:  (1.0027380590203832, 1.4966958805651132e-07, 103.0, 128.0, 346.0, 38.0)
data w1,w2,p1,p2:  (1.0027380590203832, 1.4966958805651132e-07, 103.0, 160.0, 173.0, 95.0)
data w1,w2,p1,p2:  (1.0027380590203832, 1.4966958805651132e-07, 103.0, 192.0, 173.0, 114.0)
data w1,w2,p1,p2:  (1.0027380590203832, 1.4966958805651132e-07, 103.0, 192.0, 346.0, 57.0)
data w1,w2,p1,p2:  (1.0027380590203832, 1.4966958805651132e-07, 103.0, 224.0, 173.0, 133.0)
data w1,w2,p1,p2:  (1.0027380590203832, 1.4966958805651132e-07, 103.0, 256.0, 173.0, 152.0)
data w1,w2,p1,p2:  (1.0027380590203832, 1.4966958805651132e-07, 103.0, 256.0, 346.0, 76.0)
data w1,w2,p1,p2:  (1.0027380590203832, 1.4966958805651132e-07, 103.0, 288.0, 173.0, 171.0)
data w1,w2,p1,p2:  (1.0027380590203832, 1.4966958805651132e-07, 103.0, 320.0, 346.0, 95.0)
data w1,w2,p1,p2:  (1.0027380590203832, 1.4966958805651132e-07, 160.0, 206.0, 190.0, 173.0)
data w1,w2,p1,p2:  (1.0027380590203832, 1.4966958805651132e-07, 176.0, 206.0, 209.0, 173.0)
data w1,w2,p1,p2:  (1.0027380590203832, 1.4966958805651132e-07, 192.0, 206.0, 228.0, 173.0)
data w1,w2,p1,p2:  (1.0027380590203832, 1.4966958805651132e-07, 192.0, 206.0, 346.0, 114.0)
data w1,w2,p1,p2:  (1.0027380590203832, 1.4966958805651132e-07, 192.0, 309.0, 346.0, 171.0)
data w1,w2,p1,p2:  (1.0027380590203832, 1.4966958805651132e-07, 206.0, 224.0, 346.0, 133.0)
data w1,w2,p1,p2:  (1.0027380590203832, 1.4966958805651132e-07, 206.0, 256.0, 346.0, 152.0)
data w1,w2,p1,p2:  (1.0027380590203832, 1.4966958805651132e-07, 206.0, 288.0, 346.0, 171.0)
data w1,w2,p1,p2:  (1.0027380590203832, 1.4966958805651132e-07, 206.0, 320.0, 346.0, 190.0)
data w1,w2,p1,p2:  (1.0027380590203832, 1.4966958805651132e-07, 206.0, 352.0, 346.0, 209.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 16.0, 206.0, 173.0, 19.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 32.0, 103.0, 173.0, 19.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 32.0, 206.0, 173.0, 38.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 32.0, 206.0, 346.0, 19.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 32.0, 309.0, 173.0, 57.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 64.0, 103.0, 173.0, 38.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 64.0, 103.0, 346.0, 19.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 64.0, 206.0, 173.0, 76.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 64.0, 206.0, 346.0, 38.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 64.0, 309.0, 173.0, 114.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 64.0, 309.0, 346.0, 57.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 80.0, 206.0, 173.0, 95.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 103.0, 320.0, 190.0, 173.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 103.0, 352.0, 209.0, 173.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 112.0, 206.0, 173.0, 133.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 128.0, 206.0, 173.0, 152.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 128.0, 206.0, 346.0, 76.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 128.0, 309.0, 228.0, 173.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 128.0, 309.0, 346.0, 114.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 144.0, 206.0, 173.0, 171.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 160.0, 206.0, 346.0, 95.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 160.0, 309.0, 285.0, 173.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 192.0, 309.0, 342.0, 173.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 206.0, 208.0, 247.0, 173.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 206.0, 224.0, 266.0, 173.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 206.0, 240.0, 285.0, 173.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 206.0, 256.0, 304.0, 173.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 206.0, 272.0, 323.0, 173.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 206.0, 288.0, 342.0, 173.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 256.0, 309.0, 346.0, 228.0)
data w1,w2,p1,p2:  (1.0027380590203834, 1.4966958827855592e-07, 309.0, 320.0, 346.0, 285.0)
data w1,w2,p1,p2:  (1.0027380682247937, 1.5887399862357654e-07, 253.0, 262.0, 339.0, 195.0)
data w1,w2,p1,p2:  (1.0027380698385604, 1.6048776529942188e-07, 163.0, 173.0, 218.0, 129.0)
data w1,w2,p1,p2:  (1.0027380698385604, 1.6048776529942188e-07, 173.0, 326.0, 258.0, 218.0)
data w1,w2,p1,p2:  (1.0027380698385606, 1.6048776552146649e-07, 163.0, 173.0, 258.0, 109.0)
data w1,w2,p1,p2:  (1.0027380698385606, 1.6048776552146649e-07, 163.0, 173.0, 327.0, 86.0)
data w1,w2,p1,p2:  (1.0027380698385606, 1.6048776552146649e-07, 163.0, 346.0, 258.0, 218.0)
data w1,w2,p1,p2:  (1.0027380698385606, 1.6048776552146649e-07, 163.0, 346.0, 327.0, 172.0)
data w1,w2,p1,p2:  (1.0027380698385606, 1.6048776552146649e-07, 173.0, 326.0, 327.0, 172.0)
data w1,w2,p1,p2:  (1.0027380698385606, 1.6048776552146649e-07, 326.0, 346.0, 344.0, 327.0)
data w1,w2,p1,p2:  (1.0027380727210498, 1.6337025465773536e-07, 319.0, 349.0, 357.0, 311.0)
data w1,w2,p1,p2:  (1.0027380883515551, 1.7900075999222054e-07, 161.0, 323.0, 293.0, 177.0)
data w1,w2,p1,p2:  (1.0027380883515551, 1.7900075999222054e-07, 322.0, 323.0, 354.0, 293.0)
data w1,w2,p1,p2:  (1.0027381069634589, 1.9761266378814923e-07, 168.0, 303.0, 355.0, 143.0)
data w1,w2,p1,p2:  (1.0027381069634591, 1.9761266401019384e-07, 202.0, 252.0, 355.0, 143.0)
data w1,w2,p1,p2:  (1.0027381069634591, 1.9761266401019384e-07, 303.0, 336.0, 355.0, 286.0)
data w1,w2,p1,p2:  (1.0027381210122133, 2.1166141817019479e-07, 259.0, 304.0, 337.0, 233.0)
data w1,w2,p1,p2:  (1.0027381210122133, 2.1166141817019479e-07, 266.0, 296.0, 337.0, 233.0)
data w1,w2,p1,p2:  (1.0027381273004758, 2.1794968074750898e-07, 89.0, 251.0, 158.0, 141.0)
data w1,w2,p1,p2:  (1.0027381273004758, 2.1794968074750898e-07, 89.0, 251.0, 237.0, 94.0)
data w1,w2,p1,p2:  (1.0027381273004758, 2.1794968074750898e-07, 89.0, 251.0, 282.0, 79.0)
data w1,w2,p1,p2:  (1.0027381273004758, 2.1794968074750898e-07, 178.0, 251.0, 237.0, 188.0)
data w1,w2,p1,p2:  (1.0027381273004758, 2.1794968074750898e-07, 178.0, 251.0, 282.0, 158.0)
data w1,w2,p1,p2:  (1.0027381273004758, 2.1794968074750898e-07, 178.0, 251.0, 316.0, 141.0)
data w1,w2,p1,p2:  (1.0027381273004758, 2.1794968074750898e-07, 251.0, 267.0, 282.0, 237.0)
data w1,w2,p1,p2:  (1.0027381273004758, 2.1794968074750898e-07, 251.0, 356.0, 316.0, 282.0)
data w1,w2,p1,p2:  (1.0027381288863764, 2.1953558126952544e-07, 159.0, 357.0, 244.0, 232.0)
data w1,w2,p1,p2:  (1.002738133480183, 2.2412938793792136e-07, 241.0, 272.0, 283.0, 231.0)
data w1,w2,p1,p2:  (1.0027381426108049, 2.3326000975210093e-07, 305.0, 347.0, 359.0, 294.0)
data w1,w2,p1,p2:  (1.0027381430868167, 2.3373602164866725e-07, 179.0, 223.0, 311.0, 128.0)
data w1,w2,p1,p2:  (1.0027381430868167, 2.3373602164866725e-07, 223.0, 358.0, 311.0, 256.0)
data w1,w2,p1,p2:  (1.0027381467070182, 2.3735622312059945e-07, 49.0, 142.0, 257.0, 27.0)
data w1,w2,p1,p2:  (1.0027381467070182, 2.3735622312059945e-07, 49.0, 284.0, 257.0, 54.0)
data w1,w2,p1,p2:  (1.0027381467070182, 2.3735622312059945e-07, 98.0, 142.0, 257.0, 54.0)
data w1,w2,p1,p2:  (1.0027381467070182, 2.3735622312059945e-07, 98.0, 213.0, 257.0, 81.0)
data w1,w2,p1,p2:  (1.0027381467070182, 2.3735622312059945e-07, 98.0, 284.0, 257.0, 108.0)
data w1,w2,p1,p2:  (1.0027381467070182, 2.3735622312059945e-07, 98.0, 355.0, 257.0, 135.0)
data w1,w2,p1,p2:  (1.0027381467070182, 2.3735622312059945e-07, 147.0, 284.0, 257.0, 162.0)
data w1,w2,p1,p2:  (1.0027381467070182, 2.3735622312059945e-07, 196.0, 213.0, 257.0, 162.0)
data w1,w2,p1,p2:  (1.0027381467070182, 2.3735622312059945e-07, 196.0, 284.0, 257.0, 216.0)
data w1,w2,p1,p2:  (1.0027381467070182, 2.3735622312059945e-07, 284.0, 294.0, 324.0, 257.0)
data w1,w2,p1,p2:  (1.0027381467070184, 2.3735622334264406e-07, 71.0, 98.0, 257.0, 27.0)
data w1,w2,p1,p2:  (1.0027381467070184, 2.3735622334264406e-07, 71.0, 196.0, 257.0, 54.0)
data w1,w2,p1,p2:  (1.0027381467070184, 2.3735622334264406e-07, 71.0, 294.0, 257.0, 81.0)
data w1,w2,p1,p2:  (1.0027381467070184, 2.3735622334264406e-07, 142.0, 147.0, 257.0, 81.0)
data w1,w2,p1,p2:  (1.0027381467070184, 2.3735622334264406e-07, 142.0, 196.0, 257.0, 108.0)
data w1,w2,p1,p2:  (1.0027381467070184, 2.3735622334264406e-07, 142.0, 245.0, 257.0, 135.0)
data w1,w2,p1,p2:  (1.0027381467070184, 2.3735622334264406e-07, 142.0, 294.0, 257.0, 162.0)
data w1,w2,p1,p2:  (1.0027381467070184, 2.3735622334264406e-07, 142.0, 343.0, 257.0, 189.0)
data w1,w2,p1,p2:  (1.0027381467070184, 2.3735622334264406e-07, 196.0, 355.0, 270.0, 257.0)
data w1,w2,p1,p2:  (1.0027381467070184, 2.3735622334264406e-07, 213.0, 294.0, 257.0, 243.0)
data w1,w2,p1,p2:  (1.0027381467070184, 2.3735622334264406e-07, 245.0, 284.0, 270.0, 257.0)
data w1,w2,p1,p2:  (1.0027381558838511, 2.4653305596977759e-07, 87.0, 181.0, 151.0, 104.0)
data w1,w2,p1,p2:  (1.0027381558838511, 2.4653305596977759e-07, 87.0, 181.0, 302.0, 52.0)
data w1,w2,p1,p2:  (1.0027381558838511, 2.4653305596977759e-07, 174.0, 181.0, 302.0, 104.0)
data w1,w2,p1,p2:  (1.0027381558838513, 2.465330561918222e-07, 174.0, 181.0, 208.0, 151.0)
data w1,w2,p1,p2:  (1.0027381558838513, 2.465330561918222e-07, 181.0, 261.0, 302.0, 156.0)
data w1,w2,p1,p2:  (1.0027381558838513, 2.465330561918222e-07, 181.0, 261.0, 312.0, 151.0)
data w1,w2,p1,p2:  (1.0027381558838513, 2.465330561918222e-07, 181.0, 348.0, 302.0, 208.0)
data w1,w2,p1,p2:  (1.0027381597159535, 2.5036515838294804e-07, 155.0, 215.0, 191.0, 174.0)
data w1,w2,p1,p2:  (1.0027381597159535, 2.5036515838294804e-07, 215.0, 310.0, 348.0, 191.0)
data w1,w2,p1,p2:  (1.0027381720745565, 2.6272376141278642e-07, 167.0, 307.0, 247.0, 207.0)
data w1,w2,p1,p2:  (1.0027381720745565, 2.6272376141278642e-07, 167.0, 307.0, 299.0, 171.0)
data w1,w2,p1,p2:  (1.0027381720745565, 2.6272376141278642e-07, 307.0, 334.0, 342.0, 299.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 30.0, 354.0, 119.0, 89.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 36.0, 295.0, 119.0, 89.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 45.0, 236.0, 119.0, 89.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 60.0, 177.0, 119.0, 89.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 60.0, 354.0, 238.0, 89.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 72.0, 295.0, 238.0, 89.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 90.0, 118.0, 119.0, 89.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 90.0, 236.0, 238.0, 89.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 90.0, 354.0, 357.0, 89.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 108.0, 295.0, 357.0, 89.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 118.0, 180.0, 178.0, 119.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 118.0, 270.0, 357.0, 89.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 120.0, 177.0, 238.0, 89.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 120.0, 354.0, 238.0, 178.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 135.0, 236.0, 357.0, 89.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 144.0, 295.0, 238.0, 178.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 177.0, 180.0, 267.0, 119.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 177.0, 240.0, 356.0, 119.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 180.0, 236.0, 238.0, 178.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 180.0, 354.0, 357.0, 178.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 216.0, 295.0, 357.0, 178.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 236.0, 270.0, 357.0, 178.0)
data w1,w2,p1,p2:  (1.0027381739212538, 2.6457045865235784e-07, 270.0, 354.0, 357.0, 267.0)
data w1,w2,p1,p2:  (1.002738173921254, 2.6457045887440245e-07, 59.0, 180.0, 119.0, 89.0)
data w1,w2,p1,p2:  (1.002738173921254, 2.6457045887440245e-07, 60.0, 354.0, 178.0, 119.0)
data w1,w2,p1,p2:  (1.002738173921254, 2.6457045887440245e-07, 72.0, 295.0, 178.0, 119.0)
data w1,w2,p1,p2:  (1.002738173921254, 2.6457045887440245e-07, 90.0, 236.0, 178.0, 119.0)
data w1,w2,p1,p2:  (1.002738173921254, 2.6457045887440245e-07, 90.0, 354.0, 267.0, 119.0)
data w1,w2,p1,p2:  (1.002738173921254, 2.6457045887440245e-07, 108.0, 295.0, 267.0, 119.0)
data w1,w2,p1,p2:  (1.002738173921254, 2.6457045887440245e-07, 118.0, 180.0, 238.0, 89.0)
data w1,w2,p1,p2:  (1.002738173921254, 2.6457045887440245e-07, 118.0, 270.0, 267.0, 119.0)
data w1,w2,p1,p2:  (1.002738173921254, 2.6457045887440245e-07, 120.0, 177.0, 178.0, 119.0)
data w1,w2,p1,p2:  (1.002738173921254, 2.6457045887440245e-07, 120.0, 354.0, 356.0, 119.0)
data w1,w2,p1,p2:  (1.002738173921254, 2.6457045887440245e-07, 135.0, 236.0, 267.0, 119.0)
data w1,w2,p1,p2:  (1.002738173921254, 2.6457045887440245e-07, 144.0, 295.0, 356.0, 119.0)
data w1,w2,p1,p2:  (1.002738173921254, 2.6457045887440245e-07, 177.0, 180.0, 357.0, 89.0)
data w1,w2,p1,p2:  (1.002738173921254, 2.6457045887440245e-07, 177.0, 240.0, 238.0, 178.0)
data w1,w2,p1,p2:  (1.002738173921254, 2.6457045887440245e-07, 180.0, 236.0, 356.0, 119.0)
data w1,w2,p1,p2:  (1.002738173921254, 2.6457045887440245e-07, 180.0, 354.0, 267.0, 238.0)
data w1,w2,p1,p2:  (1.002738173921254, 2.6457045887440245e-07, 216.0, 295.0, 267.0, 238.0)
data w1,w2,p1,p2:  (1.002738173921254, 2.6457045887440245e-07, 236.0, 270.0, 267.0, 238.0)
data w1,w2,p1,p2:  (1.002738173921254, 2.6457045887440245e-07, 240.0, 354.0, 356.0, 238.0)
data w1,w2,p1,p2:  (1.002738173921254, 2.6457045887440245e-07, 288.0, 295.0, 356.0, 238.0)
data w1,w2,p1,p2:  (1.002738173921254, 2.6457045887440245e-07, 295.0, 324.0, 357.0, 267.0)
data w1,w2,p1,p2:  (1.0027381845461365, 2.7519534140374446e-07, 133.0, 201.0, 215.0, 124.0)
data w1,w2,p1,p2:  (1.0027381845461365, 2.7519534140374446e-07, 133.0, 201.0, 310.0, 86.0)
data w1,w2,p1,p2:  (1.0027381845461365, 2.7519534140374446e-07, 201.0, 266.0, 248.0, 215.0)
data w1,w2,p1,p2:  (1.0027381845461365, 2.7519534140374446e-07, 201.0, 266.0, 344.0, 155.0)
data w1,w2,p1,p2:  (1.0027381845461367, 2.7519534162578907e-07, 133.0, 201.0, 172.0, 155.0)
data w1,w2,p1,p2:  (1.0027381845461367, 2.7519534162578907e-07, 201.0, 266.0, 310.0, 172.0)
data w1,w2,p1,p2:  (1.0027382066479498, 2.9729715467219364e-07, 220.0, 263.0, 326.0, 177.0)
data w1,w2,p1,p2:  (1.00273820664795, 2.9729715489423825e-07, 110.0, 263.0, 177.0, 163.0)
data w1,w2,p1,p2:  (1.00273820664795, 2.9729715489423825e-07, 220.0, 263.0, 354.0, 163.0)
Calculation took 38420.966906 seconds (10 hours, 40 minutes, 34.944842 seconds)
Total Count = 3992976100
Delta Count = 635

done
```

I'm going to run the same settings on your 3 gear clockgear and see what I get.

Sugguestions: 

1. Could you add to the output next to the seconds a parenthesis with the time data in the format I added manually,
with a space between the last results line and the "calculation took..." line?

2. Is there any way to have the results organized by closest to target first, and on down?

3. Could there be a line at the top of the results like this:
```
Target Gear Range= (1.002737909350795) (ERROR):
___________________________________________________________________________________________
``` 

Fred, I think you've created a really useful script here. This is something many people could easily use and modify for their needs. 
I know for watch & clockmakers needing special gearing ratios, this would be very useful. I could adapt this for any number of special 
astronomical phenomena, like hyper-accurate moonphase gearing. Would you think of making this available in the repositories?

---

### Post by oldfred on 2010-06-15
I did some updates to 4set version. I added a true/false line to send to file and a filename you can input at the top.
Added printout of target & error
I have a sort in there, that was why I changed from just printed to saving, sorting & outputing. The default worked for me (error exp 07 at top and err with exp 06 at bottom) but I am not sure what the default is sorting on??
I found python had a internal h:m:s that I used. Its not quite your format but easy to do.
I do not have any results from the 4 gear set version, so I still do not know if it works or not.

Do you want me to make the changes to the original 2 set & the 3 set versions also??

Updated clockgear4.py Jun 20,2010

---

### Post by BastardNamban on 2010-06-16
Yes, can you add the changes? I had clockgear4 running all night with your basic settings, and no answer. I have a feeling it will take a week to run for my settings.

It may be awhile. I wonder, is there a way to borrow unused CPU cycles from others to do calculations like this? I've heard of researchers doing this, but not individuals.

---

### Post by oldfred on 2010-06-16
I posted new versions in place of the previous versions above. I still do not know if the 4 gear works. At least the 3 gear outputted some data, but I think the version I posted I tightened up the error.

Initial runs just to test should be a range you think may give results and then tightened the error tolerance to get less results.

---

### Post by BastardNamban on 2010-06-17
Fred, I hadn't gotten results from either the 3 or 4 wheel (?) programs yet.

Can we call them by the total number of gears (ie wheels+pinions) for less confusion? And maybe rename them all in "clockgear#w#p" 
format so I can figure out which is which? I can't keep track of the code anymore! The original clockgear was 4 gears- 2 wheels, 
2 pinion. So, say, rename it to "clockgear2w2p.py", and the others too? It's just so I can keep track of which is which, since I'm 
having a hard time telling now from the code :-k :oops: It's embarrassing, but I admit it.

I've been heating my laptop too much the last week, I'll try running the new versions of the programs tommorrow (Fri)

Thanks for all the changes- I can't wait to try your new versions.

You've really gone out of your way to help me- if I can do anything for you, just ask. I'd gladly donate some $ as a "programmer's fee"
for all the time you've put into this for me.

---

### Post by oldfred on 2010-06-17
I had clockgear.py and had renamed myself to clockgear2.py for 2 sets. Then created clockgear3.py for 3 sets ( 3 each wheels & pinions) and clockgear4 for 4 sets. The name is not used anywhere in the program so you can rename to anything you want.

I have a dual processor and a panel app showing processor use and running the python programs shows 50% but I think it is a100% of one processor as python does not use both processors without additional complications. My fan comes on which it never does except at boot, so I know it is working hard.

I just would like to know if you can get results that make some sort of sense. I only test with a small range just to see that it runs, but that does not mean it runs correctly.

As I originally said I am trying to learn python and this seemed like a nice little program to try. It seems to run so I am happy. If I ever get your neck of the woods you can buy me a  beer.

---

### Post by BastardNamban on 2010-06-17
> **oldfred said:**
> 
As I originally said I am trying to learn python and this seemed like a nice little program to try. It seems to run so I am happy. If I ever get your neck of the woods you can buy me a  beer.

I'll buy you a few, deal. I'm giving my laptop a break- I'll start up clockgear4.py tomorrow evening with a small set of numbers and let you know what I get.

Got it- clockgear2 is 4 gears (2wheels2pinions), clockgear3 is 6 gears, clockgear4 is 8 gears.

---

### Post by oldfred on 2010-06-17
I do not have any error checking. For example if you made the error limit very large so it effectively outputs everything, it may crash. I store all answers in memory, then sort & output. If the number exceeds memory or maybe memory & swap it will stop working and I assume crash.

Not sure if there are any other issues I know about yet.:smile:

---

### Post by Jorge_C on 2010-06-17
Hi,

I've been following this thread and I thought this would be an interesting problem to tackle and learn a few things at the same time. I couldn't come up with any subtle way to solve it so I ended up trying to write a faster brute-force routine.

In order to do that, I used NumPy (a Python library to efficiently work with arrays) to do element-wise operations on arrays instead of using loops (the while's on the code). I'm by no means a Python programmer, I'm just learning.

For my code, I used the target ratio 1.002737909350795, an error of 2e-10, 4 pinions and 4 wheels, both starting at 40 and ending at 90.

The script took 50 minutes to run on my laptop, and returned several equivalent combinations of gears that give a ratio of 1.0027379095038731598... That's 0.0000000001530781598 or 1.5e-10 away from the true ratio. I think this is about 250 times less error than with any of the posted gears. What would be the error of the clock if this ratio was used?

So, here you have the output of my scrip (with a bit of a clean-up, first column are wheels, then pinions.):
```
[46, 47, 89, 52], [41, 53, 82, 56]
[46, 47, 89, 65], [41, 53, 82, 70]
[46, 47, 89, 78], [41, 53, 84, 82]
[47, 52, 89, 69], [41, 53, 84, 82]
[46, 47, 89, 78], [42, 53, 82, 82]
[47, 52, 89, 69], [42, 53, 82, 82]
[47, 69, 89, 78], [53, 63, 82, 82]
```

All of them produce exactly the same ratio, and the previously stated error.

By the way, if you need a calculator with an arbitrarily large precision, you can type "bc" (without the quotes) on a terminal. Then type "scale=30" and enter to set the precision to say 30 decimal figures and you're good to go.

I hope it helps.

---

### Post by BastardNamban on 2010-06-18
Dear Jorge,

Thanks for joining in! Anyone with an interest I welcome to join the discussion.

As for comparing calculation ratios, it's actually a complex question.

Read the wikis for Mean Solar Time and Sidereal Time- the number we are getting isn't constant- 
it changes over time, but by what seems to be a determinable amount per century.

It's actually going to take me a while and some math to come up with a true answer to your question 
that accounts for these changes over time.

This means taking into effect the losses and gains over a century of things like tidal friction and 
acceleration between the Earth and Moon, and other things! I am limiting my adjustments to 15 places 
behind the decimal for working purposes, and only the effects properly mentioned on the Wikipedia pages.

For clarification: The target we are working with (the 1.002737909350795 number) was the actual number of
Sideral seconds to ONE (1.000...) Mean Solar Time (Normal civil time on a clock) second in the year 2000,
which I am using as my base. 

Since my plan is to have a gear train deriving Sidereal time from Mean Solar Time, as Breguet did but 
more accurately, this means the 1.002737909350795 number becomes a ratio- of 1:1.002737909350795 for the 
gear train connecting the time displays. 

It actually changes to 1.002737909409795 Sideral seconds for every 1.00 Mean Solar Time second after 100 years. 
I have to account for these changes to calculate total true seconds, and any cumulative change.
______________________________________________________________________________________________________________

OK- Jorge, I think I have a working answer for you now:

Working Ratio (from user Jorge_C): 1 to 1.0027379095038731598 (assuming for year 2000)

Ignoring my limitation to 15 places past the decimal by adding 4 zeros to the real number:

Year 2000 JORGE_C

   WORKING Ratio = 86,400 x (1/1.0027379095038731598 )= 86164.090517679 sidereal seconds a year
-  Year 2000 Real= 86,400 x (1/1.0027379093507950000 )= 86164.090530833 sidereal seconds a year
_______________________________________________________________________________________________
=    &#8722;0.000013154 sidereal seconds a year SLOW for the year 2000.

Not bad, BUT NOT EXACT!!!  :)

To be scientific about this, I really need to re-learn significant figures and usage. I may
just take things out as far as I can get a number.

---

### Post by BastardNamban on 2010-06-18
Here's some supplemental info:

To equal number of seconds, as defined by
Mean solar time: MULTIPLY BY # of SECONDS IN A DAY (86,400)
(24 hours x 60 minutes x 60 seconds= 86,400 seconds in one Mean solar day)

Real ratio:    1 to 1.002737909350795 (As of year 2000)
Real ratio:    1 to 1.002737909409795 (As of year 2010)

Year 2000 Real= 86,400 x (1/1.002737909350795)= 86164.090530833 sidereal seconds a year
Year 2100 Real= 86,400 x (1/1.002737909409795)= 86164.090525763 sidereal seconds a year

Those are real official values.


You may be able to, with this post and the last one, figure out how your losing ratio would
perform in relation to the real values- which are a kind of constant? I have trouble wrapping
my mind around this now- I'm trying to assume that I create the base year 2000 ratio, figure
out how that changes over time, and add a planetary or starwheel to advance this by the amount
the real ratio increases yearly. Like adding a constant number to the results of a constantly
changing equation.

Ahh head hurts about to explode- very complex abstract math! I'll comprehend this fully later! Sleep now...

---

### Post by BastardNamban on 2010-06-20
To Fred (Jorge & Fred- see end)-

I ran all 3 of your clockgear builds, the new updated editions of clockgear.py, clockgear3.py, and clockgear4.py. 
For my purposes, I renamed the original files clockgear2w2p.py, clockgear3w3p.py, and clockgear4w4p.py.

The tests were ran on all 3 files- all of which I changed the target value to 1.002737909350795, and saved a separate copy of, 
truncated to shorter names for these tests- c2w2ptest.py, c3w3ptest.py, and c4w4ptest.py. These are the files I ran the tests on.

From c2w2ptest.py, with these settings:```
Target_gear_range = 1.002737909350795
error_limit = .000003
#print to file True or False uncomment(#) true to print
prt2file = False
#prt2file = True
filename = "gear2_70.csv"
#wheels starting & ending numbers
w1 = 50.
endw = 80.
#pinions starting and ending numbers
p1 = 85.
endp = 45.
```

Results are:```
 
Target Gear Range= 1.0027379094 0.0000030000
data w1-2,p1-2:  (1.0027376804380288, -2.2891276629799506e-07, 51.0, 79.0, 82.0, 49.0)
data w1-2,p1-2:  (1.0027397260273971, 1.8166766020399905e-06, 60.0, 61.0, 73.0, 50.0)
data w1-2,p1-2:  (1.0027397260273971, 1.8166766020399905e-06, 61.0, 66.0, 73.0, 55.0)
data w1-2,p1-2:  (1.0027397260273971, 1.8166766020399905e-06, 61.0, 72.0, 73.0, 60.0)
data w1-2,p1-2:  (1.0027397260273971, 1.8166766020399905e-06, 61.0, 78.0, 73.0, 65.0)
 
Total Count = 381300
Delta Count = 5

Calculation took 0.785781 seconds
Elapsed time (HH:MM:SS): 00:00:00
done
```

From c3w3ptest.py, with these settings:```
Target_gear_range = 1.002737909350795
error_limit = .0000003
#print to file True or False uncomment(#) true  to print
#prt2file = False
prt2file = True
filename = "gear3_70.csv"
#wheels starting & ending numbers
w1 = 40.
endw =61.
#pinions starting and ending numbers
p1 = 85.
endp = 65.
```

Results are:```
wheel1:  41.0  Calculation took 0.934415 seconds
wheel1:  42.0  Calculation took 1.829929 seconds
wheel1:  43.0  Calculation took 2.596326 seconds
wheel1:  44.0  Calculation took 3.282705 seconds
wheel1:  45.0  Calculation took 3.899763 seconds
wheel1:  46.0  Calculation took 4.440926 seconds
wheel1:  47.0  Calculation took 4.933375 seconds
wheel1:  48.0  Calculation took 5.343515 seconds
wheel1:  49.0  Calculation took 5.704152 seconds
wheel1:  50.0  Calculation took 6.033177 seconds
wheel1:  51.0  Calculation took 6.291577 seconds
wheel1:  52.0  Calculation took 6.509462 seconds
wheel1:  53.0  Calculation took 6.689883 seconds
wheel1:  54.0  Calculation took 6.830534 seconds
wheel1:  55.0  Calculation took 6.960086 seconds
wheel1:  56.0  Calculation took 7.043657 seconds
wheel1:  57.0  Calculation took 7.101810 seconds
wheel1:  58.0  Calculation took 7.140203 seconds
wheel1:  59.0  Calculation took 7.165074 seconds
wheel1:  60.0  Calculation took 7.176462 seconds
wheel1:  61.0  Calculation took 7.180450 seconds
<open file 'gear3_70.csv', mode 'r' at 0xb77a7128>
```

It created that file at the end- gear3_70.csv, which is some sort
of screwed up spreadsheet file, with setting data or something.
No useful results.

From c4w4ptest.py, with these settings:```
Target_gear_range = 1.002737909350795
error_limit = .000003
#print to file True or False uncomment(#) true to print
prt2file = False
#prt2file = True
filename = "gear70.csv"
#wheels starting & ending numbers
w1 = 40.
endw = 60.
#pinions starting and ending numbers
p1 = 85.
endp = 65.
```

Results are:```
wheel1:  41.0  Calculation took 41.051914 seconds
wheel1:  42.0  Calculation took 74.134817 seconds
wheel1:  43.0  Calculation took 102.746797 seconds
wheel1:  44.0  Calculation took 126.778983 seconds
wheel1:  45.0  Calculation took 146.998566 seconds
wheel1:  46.0  Calculation took 163.875082 seconds
wheel1:  47.0  Calculation took 177.875660 seconds
wheel1:  48.0  Calculation took 190.245062 seconds
wheel1:  49.0  Calculation took 199.488451 seconds
wheel1:  50.0  Calculation took 206.802178 seconds
wheel1:  51.0  Calculation took 212.328444 seconds
wheel1:  52.0  Calculation took 216.600647 seconds
wheel1:  53.0  Calculation took 219.944765 seconds
wheel1:  54.0  Calculation took 222.028216 seconds
wheel1:  55.0  Calculation took 223.424360 seconds
wheel1:  56.0  Calculation took 224.290571 seconds
wheel1:  57.0  Calculation took 224.778043 seconds
wheel1:  58.0  Calculation took 225.022369 seconds
wheel1:  59.0  Calculation took 225.119767 seconds
wheel1:  60.0  Calculation took 225.144609 seconds
 
Target Gear Range= 1.0027379094 0.0000030000
 
Total Count = 78411025
Delta Count = 0

Calculation took 225.144669 seconds
Elapsed time (HH:MM:SS): 00:03:45
done
```

Got no results. At least, unlike "clockgear3", I got a proper output, just no results. 
No file was created with this one.
________________________________________________________

And so, there you are. Something seems to be wrong with all 3 programs,
though- I changed the target value from what you originally had, but the first time around, after saving, 
I opened them again, and it had refused to save my new target value- in all 3 programs- I don't know why!

The first run of results also showed target range as your original number.

The second time around, I got the programs to save my extended target number- but this is strange- because I KNOW 
that I saved it in each, properly, the first time- so read on...

Upon editing and confirming my save to the target gear number to my extended value of 1.002737909350795, the settings 
above are posted as such with it saved, but the outputs I posted for each don't seem to reflect my new value...?

As you can see, in the first and last ones ("clockgear" and "clockgear4", renamed edits c2w2ptest.py and c4w4ptest.py), 
the output where it included the target value as it was supposed to only used YOUR value of 1.0027379094! The middle one, 
c3w3ptest.py ("clockgear3"), which didn't even print that part, had that weird file output- 
it had your 1.0027379094 value in there too!

What is going on here?

1. Why the strange file output with the middle one ("clockgear3" or c3w3ptest)- 
   instead of the normal setup for these at the end of the output?

2. What's the mysterious problem with not now taking my target value- and the three 
   programs saving mine, but using yours? How can that even be possible?

3. Can these issues be fixed, or is this a glitch or programming virus?


At least you know now- all of your programs "work"- clockgear3 and clockgear4 gave me results...

Hope we can progress from here. I am looking into renting time on a supercomputer 
at some point to crunch this stuff with high gear ranges. I'll give it a week most, when I'm
sure they are working properly- after that, it could be a guess.
_____________________________________________________

To Jorge & Fred-

I've actually contacted our USA's NOAA researchers for help calculating the extremely minute effects of tidal friction and such- 
really, just asking them where I can learn how to calculate these effects from books or texts at a higher level than wikipedia's 
jumbled numbers allow. Significant figures will apply at some point.

---

### Post by Jorge_C on 2010-06-20
First of all, thanks for the info.

I added two more gears to my code, decreased the teeth range for pinions and wheels (50 to 80 teeth), and after one hour of crunching I got a set of wheels and pinions that almost halves the error attained in my first post to 8.56790194e-11.

The five wheels are [67 68 71 71 73] and the pinions are [57 66 77 74 78]. Ratio to 15 decimal places: 1.002737909436474

This error is at the same order of magnitude than the difference between the real ratios 10 years apart:
1.002737909350795 (As of year 2000)
1.002737909409795 (As of year 2010)
1.002737909436474 (Given by these gears)

Nonetheless, I'm quite confident we could achieve an even better ratio if we used gears with more teeth. How many teeth can be used for wheels and pinions?

I've also been trying to further speed the code up, but nothing so far. I'll keep on trying, though.

---

### Post by oldfred on 2010-06-20
First I am glad that Jorge_C came up with the matrix math versions. I have to review that, as back in my day the manual calculation of matrixes  did not lead to much beyond simple and that was 45 years ago. So obviously I am not up to speed on that. My 3 set is a little long and 4 set way too long in calculation so Jorge's versions will be better.

My 2 set seems to work ok, The 3 set starts to take too long to calculate and that was why I started outputting a line on each outer gear calculated just to show it was working. If you have print to file on, it should write to a file and then print the file which should be the same format as the screen output.
this should have opened & printed to screen the printed file.
<open file 'gear3_70.csv', mode 'r' at 0xb77a7128>
 Since it is text the spreadsheet seems to be the default to open it. 

If the gear range used to calculate is too small you do not get any results. extending the accuracy of the target and not the error will not change results other than the calculation of the delta value.
The 4 set takes way too long and I think the matrix must be the way to calculate. When I was testing I would just try running with a small range but would get 0 results.

I do see the errror in  the 3 set version on writing, I forgot to save sysout, so it does not get turned back on. I can also change printout order to error first so it should sort better. But since I now am not using absolute values the smallest will be either the top or bottom depending on sign.

Replaced older versions with the updates, so no older versions are in the thread.

---

### Post by Jorge_C on 2010-08-20
After quite some time without good ideas about how to speed up the code, I managed to make it three times faster.

First, I found out that removing the np prefix from the functions inside the for loop made it about 10% faster. Then, I made the problem more symmetric by making both pinions and wheels share the same starting and ending number of teeth. This allowed me to halve the number of divisions since the ones that would yield less than one can be easily avoided. Finally, I realised I didn't really need to call "nonzero" and "logical_and" functions. After making the necessary changes to remove them, it was ~30% faster.

I also did a bit of a clean-up, added a function that predicts how long it will take to finish crunching and rewrote functions so that the now accept the number of wheels/pinions as a parameter.

The results are just printed on the terminal, maybe you'd like to have them saved to a file too?

I ran the attached script (teeth range 330-360, 10 gears) and the best result has five times less error than the previous best:
```
Wheels: [338, 341, 342, 357, 358]
Pinions: [336, 343, 344, 353, 359]
Ratio: 1.002737909331876
Ratio - 2000_true_ratio: -1.8919e-11
```

And while writing this post, I also ran the script with number=6, wi=340 and wf=360, and it returned a much better set of wheels:
```
Wheels: [345, 349, 349, 355, 355, 359]
Pinions: [344, 351, 351, 353, 354, 358]
Ratio: 1.002737909348984
Ratio - 2000_true_ratio: -1.811e-12
```

---

