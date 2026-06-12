---
title: "Emacs/ESS worth the work?"
date: 2007-05-13
forum: Education &amp; Science
---

### Post by euler_fan on 2007-05-13
I use R and have read different places that Emacs with ESS (Emacs Speak Statistics) is the "prefered"/"best" way to use it.

Right now I just use R in the terminal (after making the buffer something like 5000 lines long) and compose code in Cream for copy/paste into the terminal and archiving for reference. So far it has worked fine. I then just copy the outputs out as I get/need them.

I have messed around a little bit with Emacs, and while cool, it seems like a lot of work for anyone not editing text and working in the terminal all day long (which I don't).

So, my question is if anyone out there can advise me on whether or not it is worth learning Emacs and ESS and why/why not.

Thanks much.

---

### Post by akniss on 2007-05-14
> **euler_fan said:**
> I use R and have read different places that Emacs with ESS (Emacs Speak Statistics) is the "prefered"/"best" way to use it.

Right now I just use R in the terminal (after making the buffer something like 5000 lines long) and compose code in Cream for copy/paste into the terminal and archiving for reference. So far it has worked fine. I then just copy the outputs out as I get/need them.

I have messed around a little bit with Emacs, and while cool, it seems like a lot of work for anyone not editing text and working in the terminal all day long (which I don't).

So, my question is if anyone out there can advise me on whether or not it is worth learning Emacs and ESS and why/why not.

Thanks much.

I suppose there isn't a clear cut answer here, but I was in your shoes not too long ago.  I use R quite a bit, and it is essential that I keep my R code in a file somewhere, as I'm terrible at keeping printouts.  I was using the text editor Kate for quite a while, and it met my needs.  Someone on these forums suggested using ESS, and I gave it a try, but it was too cryptic for me.  I didn't understand how using the ESS shortcut keys was easier than just using copy/paste from Kate.  However, I kept playing with ESS, and one weekend tried to really learn all the navigation shortcuts for emacs... and I am now completely hooked.  Once your fingers 'learn' which key combination sends lines/selections to the R buffer and you get used to navigating through the file using keystrokes instead of the arrows or mouse, it is very difficult to use anything else for R script editing.  

So the short answer is it probably depends on how much you use R.  If its just a casual need every month or so, it might be difficult to keep the ESS keystrokes in your head, and would probably not be worth the effort of learning.  However, if you use R on a daily basis (sometimes for hours at a time) like me, I feel is is absolutely worth the investment of time to learn how to use ESS efficiently.

Just my 2 cents.

---

### Post by sam81 on 2007-05-14
Absolutely agree with akniss points. Plus, ESS offers some really cool features, you get used to splitting the 
window into two buffers, one with the script file your're editing, one with R running, and it's easy to send
 lines or the entire buffer from the script you're editing to the R process to evaluate your code, and go back 
and forth with just a few keystrokes.  Keep in mind that you don't have to learn Emacs all at once, you can still 
use the mouse a lot for moving and so on, and just make use of the specific ESS facilities.

Plus, you get filename and object (a function or whatever) name completion hitting the tab. I don't know 
whether other editors have this feature, but ESS has and it's really useful.

---

### Post by raja on 2007-05-14
If you are looking for an editor for R and dont want to spend the time learning ESS, another option worth looking at is [JGR]("http://rosuda.org/JGR/"). I had difficulty installing it in edgy, but have it working fine in Feisty.

---

### Post by euler_fan on 2007-05-16
Thanks everyone. I appreciate it.

I think that I will probably stick with Cream and the terminal for a while since I'm not pounding out R more than about once a month. And I'll definitely keep Emacs/ESS in the back of my mind if I ever start doing a significant amount of work in the system.

I'll take a look at JGR, but knowing myself I would just do everything CLI that I could do point and click in the GUI.

---

### Post by sgsong on 2008-01-04
Emacs+ESS also works with GUIs like Rcmdr and PMG. You can start them from within ESS and the GUI and the ESS buffer share the same data set and estimates.

---

### Post by Wittgenstein on 2008-05-22
I'm also new to this, and have a couple of questions: I try to run R in ESS and understand that R should be run in one buffer and the text-editor in another (screen split in two). Two things I don't understand: 1) what buffer should I run the text-editor in (ESS, scratch, other?), and 2) it says "everywhere" that it is so simple to send the command from the text-editing buffer to R, but how??

---

### Post by akniss on 2008-05-22
> **Wittgenstein said:**
> I'm also new to this, and have a couple of questions: I try to run R in ESS and understand that R should be run in one buffer and the text-editor in another (screen split in two). Two things I don't understand: 1) what buffer should I run the text-editor in (ESS, scratch, other?), and 2) it says "everywhere" that it is so simple to send the command from the text-editing buffer to R, but how??

This is by no means how you have to do it, but here is typically how my workflow goes:

[LIST=1]
[*]Startup emacs
[*]Ctrl + X, Ctrl + F to open a file, such as example.R.  If the file has a *.R extension, emacs will recognize it as an R script and will give you a little R button on the menu.
[*]Ctrl + X, 3 will then split the screen into 2 buffers, vertically.
[*]Ctrl + X, O will move the active cursor to the second buffer.  I then use the mouse to click on the R button on the toolbar.
[*]Ctrl + X, O to put the active cursor into the left buffer again.  I then use the left buffer as my R script, since it is the example.R file.  Type the commands I want to run, say something like ```
a<-c(1:10)
b<-rnorm(10,10,1)
t.test(a,b)
```
[*]The command Ctrl + C, Ctrl + N will then send the current line over to the R buffer.
[*]The command Ctrl + C, Ctrl + C will send the current paragraph over to the R buffer.
[*]The command Ctrl + C, Ctrl + B will send the entire buffer over to the R buffer.

[/LIST]

---

### Post by ahmatti on 2008-05-23
Once a month is probably not enough to remember all the shortcuts, but I still suggest to give it a try. I like ESS a lot, but I have to admit that when I don't use it for a few weeks I tend to forget some of the shortcuts...

I have used R with a lot of different interfaces for around a year. When I started to use R I felt that ESS was too difficult to try since I've never really used Emacs. A couple of months ago I gave it a new try and its the only interface I've used since. It definitely has been the interface to R for me!!

I started out by reading the Emacs tutorial and printing out the ESS refcard [http://ess.r-project.org/refcard.pdf](http://ess.r-project.org/refcard.pdf). After a few hours I was hooked, I really like the keyboard shortcuts! 

Even if you *don't like the shortcuts* you can use ESS quite nicely with **emacs22-gtk**, it gives you a nice menu bar with buttons to evaluate line, selected region, function or a file.  

ESS also supports Sweave ([http://www.statistik.lmu.de/~leisch/Sweave/](http://www.statistik.lmu.de/~leisch/Sweave/)), which one more reason to use it

---

### Post by Wittgenstein on 2008-05-25
Thank you akniss, but I still don't get this. In one buffer you are running R with your current file. In the other you are running a text file (right?) from where you write your commands, save the results and keep a history of what you have been doing. So you'll end up with two files, one is the R file and one is a text file.??? Am I right so far? (I've only seen this demonstrated on MS with TINN)

Okay then, what buffer should I use in the one running the text file?

I am sorry, but this is quite hard, I'm new to both R and Emacs and these tools have a really steep learning curve.:?

---

### Post by akniss on 2008-05-26
Maybe the attached image will help you understand.  The image is a screenshot of an example ess session.  The left buffer is where I keep the R script.  This buffer is simply a text file saved on my hard drive.  In this file, I put in all the R commands I need to use to enter an analyze my data.  In the screenshot, I've created two variables and fitted a linear model to the fake data.  I used the keyboard shortcuts in ESS to send the commands over to the R buffer on the right.  Now hopefully you can see the value of using this method.  The R script file on the left only contains the commands needed to do the analysis.  The interactive R buffer on the right gives you the output of the R commands as you send them from the script file.  Now you can make a change on the left side, send it to R, see the results on the right side, and change, add, and repeat as needed.

As I'm working on an analysis, I only save the R script file (left buffer).  I use ESS to make changes interactively, so that when I'm finished I've got only the commands that work and are appropriate in the R script file.  Once I've completed an analysis, I will send the entire buffer to R, and once complete will also save the R buffer (the right side) so I can print out the results of the analysis.

Hopefully this adds some clarity to the value of ESS for R.

---

### Post by plvera on 2008-05-28
Hello:

I agreee that the learning curve for both R and Emacs is rather steep. Why not concentrate on learning R then? I typically use a text editor (such as notepad in windows or gedit in ubuntu) and just copy and paste into R.

I tried Emacs for a bit but it felt cumbersome with too many things to remember. I suppose that if I were to to use it heavily every day it would become easier. However, for my purposes using a text editor works just fine.

I hope this helps.

---

### Post by Wittgenstein on 2008-08-26
In the end of the summer I've given R and ESS a new try, and now I make it work perfectly! :) Thank you akniss, you described the use of buffers very well!

Two more question:
1) When in the R-buffer, you can easily recapture earlier commands with Ctrl- arrow up/down, and this is quite handy. Is there a way to do this in the *.R buffer?
2) I save the *.R buffer as a text file. Sometimes I would like to copy-paste some output from the R-buffer in to the text file, is there some nice shortcut keys to do this?

---

### Post by akniss on 2008-08-28
> **Wittgenstein said:**
> In the end of the summer I've given R and ESS a new try, and now I make it work perfectly! :) Thank you akniss, you described the use of buffers very well!

Two more question:
1) When in the R-buffer, you can easily recapture earlier commands with Ctrl- arrow up/down, and this is quite handy. Is there a way to do this in the *.R buffer?
2) I save the *.R buffer as a text file. Sometimes I would like to copy-paste some output from the R-buffer in to the text file, is there some nice shortcut keys to do this?

I'm not aware of any easy way to do number 1.  The following will probalby answer both parts to varying degrees.  Copy & paste is done a little differently in emacs than many text editors.

A: CTRL + SPACE sets the mark

B: Once the mark is set, you can move the cursor around with the arrows or other emacs commands (such as CTRL + E, or CTRL + N, etc.)

C: CTRL + W will cut (often referred to as 'yank' by emacs users) the text between the mark set in step A and wherever the cursor currently is.

D: CTRL + Y will paste the text that was cut in step C.

If you would like to copy instead of cut, use ALT + W in step C instead of CTRL + W.  This works when switching from buffer to buffer as well.  So, you can do the following as an example.

With the cursor in the R buffer, at the beginning of the selection you would like to copy/paste:
```
CTRL + SPACE
```  will set the mark at the beginning of where you would like to copy
```
CTRL + N
```  will move the cursor to the next line (repeat until the cursor is at the end of the selection you wish to copy)
```
ALT + W
```  copies all text between the mark and the cursor
```
CTRL + X 
O
```  moves the cursor over to the *.R buffer
```
CTRL + Y
```  will paste the text into the current buffer

---

### Post by Tart on 2009-02-07
Hey All, 

I just decided to give a try to EMACS+ESS, and almost immediatly discoverd a problem, well it maybe only problem for me. I cannot get underscore while editing, every time I press Shift+"-" to get "_" I get "<-". 

Where can I edit shortcuts for ESS?

Thanks

---

### Post by ahmatti on 2009-02-07
> **Tart said:**
>  I cannot get underscore while editing, every time I press Shift+"-" to get "_" I get "<-". 

Where can I edit shortcuts for ESS?


I don't know about editing shortcuts, but you can get underscore by pressing Shift+"-"+"-" i.e type the dash twice. I actually find the shortcut for "<-" a very convinient for writing clean code. If I remember correctly R doesn't allow "_" in varible names anyway.

---

### Post by Tart on 2009-02-07
Thanks for your reply, it works perfectly. Note: R allows both "_" and "." in variable names.

---

### Post by itaylor on 2009-02-23
I'm slowly moving to emacs from jedit and finding it to be a mix of great features that I didn't know how much I was missing, and arcane specifications that I find frustrating.

These ergonomic keybindings helped: [http://xahlee.org/emacs/ergonomic_emacs_keybinding.html](http://xahlee.org/emacs/ergonomic_emacs_keybinding.html), as they also reduce the learning curve by allowing some common keyboard shortcuts.



> **Tart said:**
> Thanks for your reply, it works perfectly. Note: R allows both "_" and "." in variable names.

This has been the case for a number of years, and I find the double-underscore shortcut tedious. Luckily emacs has adapted to the change in R's treatment of the underscore. I was able to get things working in a way I liked by adding these lines to my init.el (.emacs) file:

```
;; change assignment operator shortcut
(ess-toggle-underscore nil)
(ess-toggle-S-assign-key t)
```

That remove the underscore mapping and uses C-= (control-equals) as the shortcut for the assignment operator.

I think it's also possible to replace C-= as the ess-S-assign-key, but I didn't try that.

A discussion of the development of this option is at [https://stat.ethz.ch/pipermail/ess-help/2006-March/003380.html](https://stat.ethz.ch/pipermail/ess-help/2006-March/003380.html)

---

### Post by dlebauer on 2009-11-12
> **Tart said:**
> Hey All, 

I just decided to give a try to EMACS+ESS, and almost immediatly discoverd a problem, well it maybe only problem for me. I cannot get underscore while editing, every time I press Shift+"-" to get "_" I get "<-". 

Where can I edit shortcuts for ESS?

Thanks

Here is a link for customizing ESS
[http://ess.r-project.org/Manual/ess.html#Customization](http://ess.r-project.org/Manual/ess.html#Customization)

But if you want an underscore, just hit Shift+"-"+"-", i.e. hit the "-" button twice and it changes from <- to _

hope that helps

-David

---

