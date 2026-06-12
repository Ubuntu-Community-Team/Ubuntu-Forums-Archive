---
title: "HOWTO: Hack (change variables) games with scanmem"
date: 2008-11-28
forum: Gaming &amp; Leisure
---

### Post by runemaste644 on 2008-11-28
If you are using Linux and miss Cheat Engine, you can use scanmem alternatively. I have made a tutorial on how to use it. Scanmem is PERFECT for hacking flash games online, but cannot hack things in which data is stored on a server. In a future edit, I plan to make a list of good hackable games. Please post your success stories.

[B]Step 1: Install scanmem if you haven't already.
[/B]
Scanmem is in the Ubuntu repositories. An appropriate command would be:
```
sudo apt-get install scanmem
```You may, of course substitute aptitude for apt-get if you wish.

**Step 2: Start scanmem in a terminal.**

The command to start scanmem is:
```
scanmem
```**Step 3: Find the ID of the process you want to hack.**

Go to System->Administration->System Monitor, scroll down until you find the process you want (Ex. firefox) and find the number under the ID column. (Ex. 5238)
Now go back to the terminal running scanmem and type:
```
pid <ID of process>
```Of course, you put the ID number in place of the <ID of process>.

[B]Step 4: Find the value of the variable you want to change.
[/B]
Simply find the value and type it in to scanmem's terminal and press enter. Just the number. You may also want to do an = sign a few times to narrow down the thousands of results you probably came up with.

[B]Step 5: Change the variable some to make scanmem narrow it down more.
[/B]
You need to continue playing and pause frequently to make scanmem acknowledge it. If you make the variable larger, type a > sign and hit enter. If you make it smaller, type < and hit enter. If the variable doesn't change, = then enter. Keep doing this until you get the message:
```
info: we currently have 1 matches.
info: match identified, use "set" to modify value.
info: enter "help" for other commands.

```**Step 6: Set the variable to what you want.**

All you need to do now is set the variable. Type in something like:
```
set 9999999
```All done! If you couldnt find the variable, repeat step 4-6, but this time multiply the value by 8. And when you set the variable to what you want, it has to be a multiple of 8 too.

---

### Post by Aqlor on 2010-09-05
What if you don't know the original value of the variable? For example many games have an health bar. You may or may not know the value.
So, is there a way to search for unknown values and narrow the search by using the < , > and = symbols ?

---

### Post by pepsifx357 on 2010-12-16
Can you use exact values to find the process like:

< 28 for saying, now the process has 28 less than it did.

Or > 5 for saying, the process has a value that is 5 more?

---

### Post by floydfan on 2011-01-02
What is the variable for speed of Firefox in this program? I only want to slow down the execution speed to a tenth of the original. I want to play the game but at my speed not theirs. With CheatEngine, I could do this in windoze using IE and Chrome. I never used Firefox on Windoze as I don't like it and like IE it gets fussy and sloooooow.

---

