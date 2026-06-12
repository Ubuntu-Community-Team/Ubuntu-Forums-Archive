---
title: "Ubuntu mate 17.04 custom date format"
date: 2017-06-15
forum: Desktop Environments
---

### Post by sorinux2 on 2017-06-15
Hello,
Recently I installed Ubuntu Mate 17.04.
the first thing I tried to do was to change the format of the date. I found some threads, dating a few editions back, but it seems those instruction do not work any longer for this version.
I tried to edit  [FONT=Ubuntu, Droid Sans, Helvetica, sans-serif]/org/mate/panel/objects/clock/prefs, also I used dconf, but no success.
is there a new way to edit the format of the time and date?[/FONT]

---

### Post by deadflowr on 2017-06-15
Moved to *Desktop Environments*

---

### Post by #&amp;thj^% on 2017-06-15
> **sorinux2 said:**
> Hello,
Recently I installed Ubuntu Mate 17.04.
the first thing I tried to do was to change the format of the date. I found some threads, dating a few editions back, but it seems those instruction do not work any longer for this version.
I tried to edit  [FONT=Ubuntu]/org/mate/panel/objects/clock/prefs, also I used dconf, but no success.
is there a new way to edit the format of the time and date?[/FONT]

What exactly are you trying to change?
Give us a clue, for example to change 24hr to 12hr, Time Zone, What is displayed days, weeks, minutes , seconds.
And have you looked at the Control Panel>>>Under the System Menu.
EDIT: Ok I just read this again,you will have to change the format from 24 hours to** "custom" **with Dconf-editor


Step 2:
Than change it at /org/mate/panel/objects/clock/prefs/ custom-format to [B]"%a %H:%M %m/%d/%Y"
[/B]Or the format you want to show.
And the result to panel clock: format should change immediately after you press enter at dconf-editor "custom-format"

---

### Post by sorinux2 on 2017-06-18
@1fallen: that's why I wrote "custom date format".
I tried again to change it, where you said also. I would like to have something like: %dddd , %Wkww, %dd-%MMMM-%Y. Again, no success.
I should have mention in the beginning, that I get the following message: No schema found.
Can somebody understand what is wrong?

---

### Post by #&amp;thj^% on 2017-06-18
> **sorinux2 said:**
> @1fallen: that's why I wrote "custom date format".

Yes my edit should have shown you I understand that now. ;)
With dconf-editor you first need to change the value to "custom"
Then ok the change....then enter the format you choose.
I use this format for myself: < %a %I:%M %m/%d/%Y>

Here is some good references to Date and Time formats: [URL="http://www.csharp-examples.net/string-format-datetime/"]http://www.csharp-examples.net/string-format-datetime/



[/URL]

---

### Post by sorinux2 on 2017-06-19
And again... no change!

---

### Post by Dennis N on 2017-06-19
I also get the "no schema found" message, but I was able to change the format anyway. In post #4, you show a pattern, but in the editor, you can't enter a pattern, you have to use the codes to produce the pattern you want. Another reference is the strftime(3) man page at:

[http://man7.org/linux/man-pages/man3/strftime.3.html](http://man7.org/linux/man-pages/man3/strftime.3.html)

To reiterate what 1fallen has said, you need to make two changes, shown in the attached image.

---

### Post by sorinux2 on 2017-06-20
This is getting a little too technical for me.
I do not know what or where is this "strftime(3)".
Offff... it was so easy to change before....
thank you for your help!

---

### Post by Dennis N on 2017-06-20
> This is getting a little too technical for me.
In that case you could give an example of a date written in your preferred custom format, and someone might give you the correct code to use in the dconf editor dialog.

---

### Post by sorinux2 on 2017-06-23
> **Dennis N said:**
> In that case you could give an example of a date written in your preferred custom format, and someone might give you the correct code to use in the dconf editor dialog.

Dennis, I wrote above what format I was using before. This is the format I was using for over 2 years (not on Ubuntu), but was working without any problem.

---

### Post by #&amp;thj^% on 2017-06-23
> **sorinux2 said:**
> Dennis, I wrote above what format I was using before. This is the format I was using for over 2 years (not on Ubuntu), but was working without any problem.

Well this dose not work for me..**." %dddd , %Wkww, %dd-%MMMM-%Y" **:(   (Shows some oddities)
But mine works...**."%a %I:%M %m/%d/%Y"**
You may "now" need to play around with yours from the links we have given you. (To get it to work)
Don't know what or if anything has changed to prevent yours from working though.
Here is Great site to help with working format for you: [http://www.foragoodstrftime.com/](http://www.foragoodstrftime.com/)
It will help you create your own custom format just drag and drop and easy peasy.

---

### Post by Dennis N on 2017-06-24
> **sorinux2 said:**
> Dennis, I wrote above what format I was using before. This is the format I was using for over 2 years (not on Ubuntu), but was working without any problem.

The strf standard clock format codes Ubuntu uses are a % followed by a single letter. If more characters than a single letter are used after a %, including spaces, then those are not treated as code to interpret and just copied as-is.

**%d** gives the date 
24
but **%dddd** gives date and three letter d's
24ddd 
only the first d is treated as code.
**Today is the %dth** will give 
Today is the 24th


Google **strf clock codes** and you will find lots of documentation and examples.

---

