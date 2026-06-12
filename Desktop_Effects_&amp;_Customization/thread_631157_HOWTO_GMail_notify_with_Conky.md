---
title: "HOWTO: GMail notify with Conky"
date: 2007-12-04
forum: Desktop Effects &amp; Customization
---

### Post by staticvoid on 2007-12-04
I've been looking for a a way to do this forever. I finally figured it out!!

**Reqierments:**
conky
python

**Ingredients:**
2 files
.conkyrc in ~/
and
gmail.py in ~/.scripts
[B]
Lets Go![/B]

If you have not all ready, make a .conkyrc file in your home directory.

Here's mine:
```
background yes
use_xft no
xftfont Bitstream Vera Sans:size=7
xftalpha 0.8
update_interval 0.5
own_window yesEdit/Delete Message
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_border no
draw_graph_borders yes
stippled_borders no
default_color white
default_shade_color black
alignment top_right
minimum_size 1425
maximum_width 1050
gap_y 32
gap_x 32
use_spacer no
no_buffers yes

TEXT
${color white} Processor - ${cpu cpu0}% ${cpugraph cpu1 8, 30 ffffff ffffff}  | Memory - ${mem} of ${memmax} ${memgraph mem 8, 30 ffffff ffffff} | Processes - $running_processes of $processes running | HDD - ${fs_used /} of ${fs_size /} used | Mail - ${color 95956B}${execi 300 python ~/.scripts/gmail.py} ${color FFFFFF}
```
[B]
Notice the last line:[/B]
>  Mail - ${color 95956B}${execi 300 python ~/.scripts/gmail.py} ${color FFFFFF}

Now make a folder in your home directory called .scripts and make a file in that directory called gmail.py

gmail.py says:
```
import os
import string

#Enter your username and password below within double quotes
# eg. username="username" and password="password"
username="username"
password="********"

com="wget -O - https://"+username+":"+password+"@mail.google.com/mail/feed/atom --no-check-certificate"

temp=os.popen(com)
msg=temp.read()
index=string.find(msg,"<fullcount>")
index2=string.find(msg,"</fullcount>")
fc=int(msg[index+11:index2])

if fc==0:
   print "0 new"
else:
   print str(fc)+" new"
```

And fill in your info. Do NOT edit the following, as it receives the variables you have previously defined :D

> 
com="wget -O - https://"+username+":"+password+"@mail.google.com/mail/feed/atom --no-check-certificate"

There you have it!!  :D  killall conky & conky

Hope it works for you. Seems to work for me. Not so sure about it working with thunderbird though...hmmm. 

tell me ways to fix this if it doesn't work :)


sv------------------------**[SIZE="3"]2nd tutorial[/SIZE]**
_***For a little more informative notifier***_

lvleph, here is your hard work from page 3, just thought i'd bring it up top :)
I added the addition of a "From User:" line. Also, I have it so that I run the original script that just outputs the number of new messages. This way I can have that in a different color.


**gmail.py**

```
import os
import string

#Enter your username and password below within double quotes
# eg. username="username" and password="password"
username="<username>"
password="<password>"

com="wget -O - https://"+username+":"+password+"@mail.google.com/mail/feed/atom --no-check-certificate"

temp=os.popen(com)
msg=temp.read()
index=string.find(msg,"<fullcount>")
index2=string.find(msg,"</fullcount>")
fc=int(msg[index+11:index2])

if fc==0:
   print "no"
else:
   print str(fc)
```

**gmail_subj.py**

```
import os
import string

#Enter your username and password below within double quotes
# eg. username="username" and password="password"
username="<username>"
password="<password>"

com="wget -O - https://"+username+":"+password+"@mail.google.com/mail/feed/atom --no-check-certificate"

temp=os.popen(com)
msg=temp.read()
index=string.find(msg,"<fullcount>")
index2=string.find(msg,"</fullcount>")
fc=int(msg[index+11:index2])

if fc==0:
   print ""
else:
   # vars
   intChars = 35 # the number of characters displayed of long subjects
   intLimitedSubjects = 0 # 0,1 - disable,enable limiting of displayed subjects
   intSubjects = 2 # subjects to display if limiting of displayed subjects is enabled

   # open the output to read
   temp=os.popen(com)
   msg=temp.read()
   
   # find and display the subjects of the messages
   for i in range(1,fc+1): # run for every new email message
      # find...
      if i != 1: # delete part of the output that has been searched
         msg=msg[index2+17:]
      index=string.find(msg,"<entry><title>")
      index2=string.find(msg,"</title><summary>")
      fs=msg[index+14:index2]
      msg=msg[index2+15:]
      index=string.find(msg,"<author><name>")
      index2=string.find(msg,"</name><email>")
      ff=msg[index+14:index2]
      # these 3 rules are a modification of their original counterparts

      # display...
      message = "\"" + fs[:intChars] # display " and first 35 chars of subject
      if len(fs) > intChars:
         message += "..." # add '...' when subject is longer than 35 chars
      print "From " + ff + ":\n" + message + "\"" # add the end " to the message

      # Limiting of displayed subjects
      if intLimitedSubjects == 1:
         if i >= intSubjects:
            print str(intSubjects) + " out of " + str(fc) + " new messages shown."
            break
         else:
            continue
      else:
         continue
```

**gmail section of .conkyrc**

```
${color1}GMail:	${color}You have ${color3}${texeci 100 python ~/scripts/gmail.py} ${color}new email(s).
${execi 100 python ~/scripts/gmail_subj.py}
```


**LINKS TO OTHER HELPFUL GMAIL + CONKY STUFF:**
[http://ubuntuforums.org/showthread.php?p=4219577#post4219577](http://ubuntuforums.org/showthread.php?p=4219577#post4219577)


and there you have it :D woohoo for python, conky, and gmail!!

---

### Post by stalker145 on 2007-12-04
This worked perfectly. Thank you much.

---

### Post by staticvoid on 2007-12-04
yay :) I'm glad it worked. How proud i feel. my second "howto"

hasta luego,

sv

---

### Post by ncappel1 on 2007-12-08
This is great, now my compulsive email checking will be reduced significantly. 

Is it possible to have it be the standard color when there are 0 new messages, and another color when there are new messages?

---

### Post by staticvoid on 2007-12-08
before I start to awnser your question: I don't know how. ;)
>  Is it possible to have it be the standard color when there are 0 new messages, and another color when there are new messages?
sure, notice this last line of code in the python script file?
```
if fc==0:
   print "0 new"
else:
   print str(fc)+" new"
```

the python code for coloring a string is:
```
 color='black'
```

Now, I do not speak python, so that's about as far as I can help you, but you would add this color value to the string (or a different value, perhaps 'red'?), or you may need to add it to the class... I'm not sure where that is...

So, if someone with knowledge of python could post here, I'd be happy to add this to my howto :) I think its very useful


sv

---

### Post by Tuning_In on 2007-12-19
Thanks. Worked great:)

---

### Post by staticvoid on 2007-12-20
so, anybody here know some python to implement  it into the code?

To make new massages a different color?

thanks!

And your welcome Tuning_in!  :) Glad it was useful
btw, your ubuntu search, have you tried uboontu.com ? its cool :D

sv

---

### Post by Gigamo on 2007-12-28
this doesn't work for me; i get this error:

```
https://(my username is filled in here):(and my password here)@mail.google.com/mail/feed/atom: Bad port number.
Traceback (most recent call last):
  File "/home/gigamo/scripts/gmail.py", line 15, in <module>
    fc=int(msg[index+11:index2])
ValueError: invalid literal for int() with base 10: ''

```

---

### Post by staticvoid on 2007-12-29
#Enter your username and password below within double quotes
# eg. username="username" and password="password"
username="username"
password="********"

did you leave the quotes?
what do you have on line 15 of your gmail.py file?

---

### Post by Spitphire on 2007-12-29
also noticed if you have an @ symbol in your password seems to cause problems...

other than that great script and add-on!  thanks much!

Alex

---

### Post by Gigamo on 2007-12-29
> **staticvoid said:**
> #Enter your username and password below within double quotes
# eg. username="username" and password="password"
username="username"
password="********"

did you leave the quotes?
what do you have on line 15 of your gmail.py file?

Yes I left the quotes.

Line 15 is this:

```
fc=int(msg[index+11:index2])
```

---

### Post by staticvoid on 2007-12-29
try it without the quotes, make sure the your gmail account is enabled for POP3 and check over the tutorial again (e.g. make sure you have a .scripts folder and what not)

:) hope you get it figured out, i wish i was proficiant in python enough to help you more.

---

### Post by Gigamo on 2007-12-29
I got it figured out now. Under username I had previously entered "****@gmail.com". I replaced it with just "****" (where **** is my actual username), and now it seems to be working. Thanks!

---

### Post by staticvoid on 2007-12-29
cool :)

i think i had that error aswell at first... lol

---

### Post by Choxo on 2007-12-30
Is there a possibility to define a fetch time?
How many times does this scripts updates itself?

Thanks!

---

### Post by staticvoid on 2007-12-30
In this method fetch times are independent of the script I figure its whenever the feed gets updated

> com="wget -O - https://"+username+":"+password+"@mail.google.com/mail/feed/atom

as for when it retreves the info...? can;t help you their. I don't see any implications in the python file. the conkyrc should get updated every few seconds with sys info. we have three information transfers going on, feed to script to conky

wish i could help you. I'm still waiting on a python guru to post some help here! :D

static

---

### Post by lvleph on 2008-01-01
> **Spitphire said:**
> also noticed if you have an @ symbol in your password seems to cause problems...

other than that great script and add-on!  thanks much!

Alex

In place of an @ put %40 and it should work.

I think I am going to have to work on this so that it actually displays the message too. I like your simple script it is nice.

---

### Post by staticvoid on 2008-01-02
cool, hey you should post it if you figure it out :)

oh and if you read back aways we were struggling to figure out how to change the color of new mail and such... tu hablas python? :)

sv

---

### Post by lvleph on 2008-01-02
I don't know python, but I know Perl and they seems very similar, so... Changing the color of the new mail can be done by 

```
You have ${color ######}${execi 6000 ~/.scripts/gmail.py} ${color}new email(s).
```

Is that what you meant. But you would have to change the script slightly so that all it ouputs is the number of emails. In this ${color ######} represents some color of your choice and ${color} is your default color.

Oh and the update time on the script is in the case I wrote above is 60 seconds.

---

### Post by Goofy666 on 2008-01-04
(Ugh, Firefox was gone, suddenly... And I just finished my post. Darn. It won't be as long this time...)

If you want the script to merely return an integer, being the amount of new messages, just remove the (addition of the) 'new' strings at the end. But that won't help much either, since Conky doesn't have some sort of full if-else statement that can be used, and certainly not for spitting out configuration tags rather than strings that will be displayed instead of interpreted.

Anyway, I spent a couple of hours extending the script. It now shows (a part of) the subjects of (a number of) new emails. Looks (quotes, list format, email address, ...) can be modified with (small) code changes. I'll post the contents of the updated gmail.py (gmail_extended.py), and the entries I am using in my .conkyrc.

**gmail_extended.py**:
```
import os
import string

#Enter your username and password below within double quotes
# eg. username="username" and password="password"
username="<username>"
password="<password>"

com="wget -O - https://"+username+":"+password+"@mail.google.com/mail/feed/atom --no-check-certificate"

temp=os.popen(com)
msg=temp.read()
index=string.find(msg,"<fullcount>")
index2=string.find(msg,"</fullcount>")
fc=int(msg[index+11:index2])

if fc==0:
   print "No new messages."
else:
   # vars
   intChars = 35 # the number of characters displayed of long subjects
   intLimitedSubjects = 0 # 0,1 - disable,enable limiting of displayed subjects
   intSubjects = 2 # subjects to display if limiting of displayed subjects is enabled
   
   # display the amount of messages
   if fc > 1: # if there are multiple messages, make 'messages' plural
      plural = 's'
   else:
      plural = ''
   print str(fc) + " new message" + plural + ":"

   # open the output to read
   temp=os.popen(com)
   msg=temp.read()
   
   # find and display the subjects of the messages
   for i in range(1,fc+1): # run for every new email message
      # find...
      if i != 1: # delete part of the output that has been searched
         msg=msg[index2+17:]
      index=string.find(msg,"<entry><title>")
      index2=string.find(msg,"</title><summary>")
      fs=msg[index+14:index2]
      # these 3 rules are a modification of their original counterparts

      # display...
      message = "\"" + fs[:intChars] # display " and first 35 chars of subject
      if len(fs) > intChars:
         message += "..." # add '...' when subject is longer than 35 chars
      print message + "\"" # add the end " to the message

      # Limiting of displayed subjects
      if intLimitedSubjects == 1:
         if i >= intSubjects:
            print str(intSubjects) + " out of " + str(fc) + " new messages shown."
            break
         else:
            continue
      else:
         continue
```**entries in .conkyrc**:
```
${offset 10}${alignr}${color0}<username1>@gmail.com
${offset 10}${alignr}${color1}${execi 300 python ~/.scripts/gmail_extended.py}

${offset 10}${alignr}${color0}<username2>@gmail.com
${offset 10}${alignr}${color1}${execi 300 python ~/.scripts/gmail_extended2.py}
```As you can see on the part of the screenshot which I attached (and in the code) I am monitoring two Gmail accounts. This is as simple as copying gmail_extended.py, renaming it (e.g. gmail_extended2.py) and using it in another entry in .conkyrc. This works for the original gmail.py as well btw!

Please let me know if the code could be better. I am by no means a Python/programming expert, and I tend not to use the possibilities that some programming  languages offer when I should. This file will probably be in constant development, if you guys/girls are interested I'll keep you updated on any changes - if staticvoid would ever make an OS project out of this I would be happy to contribute where I can ;p.

---

### Post by lvleph on 2008-01-04
Man I didn't even get to it yet. You are certainly faster than I am, but I was still trying to get other things to work, like weather. Nice job.

---

### Post by lvleph on 2008-01-04
Well, I decided to add onto the work done by staticvoid and Goofy666. I added the addition of a "From User:" line. Also, I have it so that I run the original script that just outputs the number of new messages. This way I can have that in a different color.

**gmail.py**
```
import os
import string

#Enter your username and password below within double quotes
# eg. username="username" and password="password"
username="<username>"
password="<password>"

com="wget -O - https://"+username+":"+password+"@mail.google.com/mail/feed/atom --no-check-certificate"

temp=os.popen(com)
msg=temp.read()
index=string.find(msg,"<fullcount>")
index2=string.find(msg,"</fullcount>")
fc=int(msg[index+11:index2])

if fc==0:
   print "no"
else:
   print str(fc)
```

**gmail_subj.py**
```
import os
import string

#Enter your username and password below within double quotes
# eg. username="username" and password="password"
username="<username>"
password="<password>"

com="wget -O - https://"+username+":"+password+"@mail.google.com/mail/feed/atom --no-check-certificate"

temp=os.popen(com)
msg=temp.read()
index=string.find(msg,"<fullcount>")
index2=string.find(msg,"</fullcount>")
fc=int(msg[index+11:index2])

if fc==0:
   print ""
else:
   # vars
   intChars = 35 # the number of characters displayed of long subjects
   intLimitedSubjects = 0 # 0,1 - disable,enable limiting of displayed subjects
   intSubjects = 2 # subjects to display if limiting of displayed subjects is enabled

   # open the output to read
   temp=os.popen(com)
   msg=temp.read()
   
   # find and display the subjects of the messages
   for i in range(1,fc+1): # run for every new email message
      # find...
      if i != 1: # delete part of the output that has been searched
         msg=msg[index2+17:]
      index=string.find(msg,"<entry><title>")
      index2=string.find(msg,"</title><summary>")
      fs=msg[index+14:index2]
      msg=msg[index2+15:]
      index=string.find(msg,"<author><name>")
      index2=string.find(msg,"</name><email>")
      ff=msg[index+14:index2]
      # these 3 rules are a modification of their original counterparts

      # display...
      message = "\"" + fs[:intChars] # display " and first 35 chars of subject
      if len(fs) > intChars:
         message += "..." # add '...' when subject is longer than 35 chars
      print "From " + ff + ":\n" + message + "\"" # add the end " to the message

      # Limiting of displayed subjects
      if intLimitedSubjects == 1:
         if i >= intSubjects:
            print str(intSubjects) + " out of " + str(fc) + " new messages shown."
            break
         else:
            continue
      else:
         continue
```
.
**gmail section of .conkyrc**
```
${color1}GMail:	${color}You have ${color3}${texeci 100 python ~/scripts/gmail.py} ${color}new email(s).
${execi 100 python ~/scripts/gmail_subj.py}
```

---

### Post by Goofy666 on 2008-01-04
Nice job! I will be adding your code to the files in .scripts.

I have come across a screenshot + homemade code for a weather plugin, but I can't find it in my bookmarks.

A link to another option that seems to work can be found here: [http://www.linuxforums.org/forum/linux-applications/46636-conky-weather-script.html](http://www.linuxforums.org/forum/linux-applications/46636-conky-weather-script.html). With the [nwsweather.tar.gz]("http://www.meteor.iastate.edu/~bschwedl/nwsweather.tar.gz") it should be possible to integrate a weather-plugin in Conky fairly easy.

(And again, thanks for noticing that I wasn't paying attention!)

---

### Post by lvleph on 2008-01-04
I made a fix in my gmail_subj.py, because I was getting an extra line when there were no emails.

**gmail_subj.py**
```
import os
import string

#Enter your username and password below within double quotes
# eg. username="username" and password="password"
username=<username>
password=<password>

com="wget -O - https://"+username+":"+password+"@mail.google.com/mail/feed/atom --no-check-certificate"

temp=os.popen(com)
msg=temp.read()
index=string.find(msg,"<fullcount>")
index2=string.find(msg,"</fullcount>")
fc=int(msg[index+11:index2])

if fc>0:
   # vars
   intChars = 35 # the number of characters displayed of long subjects
   intLimitedSubjects = 1 # 0,1 - disable,enable limiting of displayed subjects
   intSubjects = 3 # subjects to display if limiting of displayed subjects is enabled

   # open the output to read
   temp=os.popen(com)
   msg=temp.read()
   
   # find and display the subjects of the messages
   for i in range(1,fc+1): # run for every new email message
      # find...
      if i != 1: # delete part of the output that has been searched
         msg=msg[index2+17:]
      index=string.find(msg,"<entry><title>")
      index2=string.find(msg,"</title><summary>")
      fs=msg[index+14:index2]
      index=string.find(msg,"<author><name>")
      index2=string.find(msg,"</name><email>")
      ff=msg[index+14:index2]
      # these 3 rules are a modification of their original counterparts

      # display...
      message = "\"" + fs[:intChars] # display " and first 35 chars of subject
      if len(fs) > intChars:
         message += "..." # add '...' when subject is longer than 35 chars
      print "From " + ff + ":\n" + message + "\"" # add the end " to the message

      # Limiting of displayed subjects
      if intLimitedSubjects == 1:
         if i > intSubjects:
            print str(intSubjects) + " out of " + str(fc) + " new messages shown."
            break
         else:
            continue
      else:
         continue
print ""
```

Oh and the weather thing, I am working on a better one that doesn't require the xlst crap.

---

### Post by Goofy666 on 2008-01-04
Nice :) keep 'em coming!

> **lvleph said:**
> Oh and the weather thing, I am working on a better one that doesn't require the xlst crap.

Hm, good plan. I was looking for another weather script, since the NWS only supplies info about the USA, at least that's I conclude from the info I found about it. Maybe I should look after a suitable online weather service for Europe, and try to make a script for it. Do you have an idea from which weather service you will be getting the data from?

---

### Post by lvleph on 2008-01-04
> **Goofy666 said:**
> Nice :) keep 'em coming!



Hm, good plan. I was looking for another weather script, since the NWS only supplies info about the USA, at least that's I conclude from the info I found about it. Maybe I should look after a suitable online weather service for Europe, and try to make a script for it. Do you have an idea from which weather service you will be getting the data from?

[This is the one I am basing mine on](http://www.gnome-look.org/content/show.php/new+vision+of+conky?content=70929). I just want to add a preview for tomorrows weather. The code is all in Polish. I am essentially rewriting the whole thing. That will be for a separate thread, I don't want this one to go off topic.

---

### Post by RavUn on 2008-01-05
EDIT: I got it working now... my password had a # in it and I changed it so there's no # any longer and it works...

Thanks!!


Original post:


I'm getting the following when trying to use lvleph's code:

```
https://((USERNAME)):((PASSWORD))@mail.google.com/mail/feed/atom: Bad port number.
https://((USERNAME)):((PASSWORD))@mail.google.com/mail/feed/atom: Bad port number.
Traceback (most recent call last):
  File "/home/ravun/.scripts/gmail_subj.py", line 15, in <module>
    fc=int(msg[index+11:index2])
ValueError: invalid literal for int() with base 10: ''
Traceback (most recent call last):
  File "/home/ravun/.scripts/gmail.py", line 15, in <module>
    fc=int(msg[index+11:index2])
ValueError: invalid literal for int() with base 10: ''

```

Here's my gmail_subj.py (All I changed from the original was the UN/PW part...):
```

import os
import string

#Enter your username and password below within double quotes
# eg. username="username" and password="password"
username="MyUsername"
password="MyPassword"

com="wget -O - https://"+username+":"+password+"@mail.google.com/mail/feed/atom --no-check-certificate"

temp=os.popen(com)
msg=temp.read()
index=string.find(msg,"<fullcount>")
index2=string.find(msg,"</fullcount>")
fc=int(msg[index+11:index2])

if fc>0:
   # vars
   intChars = 35 # the number of characters displayed of long subjects
   intLimitedSubjects = 1 # 0,1 - disable,enable limiting of displayed subjects
   intSubjects = 3 # subjects to display if limiting of displayed subjects is enabled

   # open the output to read
   temp=os.popen(com)
   msg=temp.read()
   
   # find and display the subjects of the messages
   for i in range(1,fc+1): # run for every new email message
      # find...
      if i != 1: # delete part of the output that has been searched
         msg=msg[index2+17:]
      index=string.find(msg,"<entry><title>")
      index2=string.find(msg,"</title><summary>")
      fs=msg[index+14:index2]
      index=string.find(msg,"<author><name>")
      index2=string.find(msg,"</name><email>")
      ff=msg[index+14:index2]
      # these 3 rules are a modification of their original counterparts

      # display...
      message = "\"" + fs[:intChars] # display " and first 35 chars of subject
      if len(fs) > intChars:
         message += "..." # add '...' when subject is longer than 35 chars
      print "From " + ff + ":\n" + message + "\"" # add the end " to the message

      # Limiting of displayed subjects
      if intLimitedSubjects == 1:
         if i > intSubjects:
            print str(intSubjects) + " out of " + str(fc) + " new messages shown."
            break
         else:
            continue
      else:
         continue
print ""
```

and here is my gmail.py (all I changed was the UN/PW part here, too):
```

import os
import string

#Enter your username and password below within double quotes
# eg. username="username" and password="password"
username="MyUsername"
password="MyPassword"

com="wget -O - https://"+username+":"+password+"@mail.google.com/mail/feed/atom --no-check-certificate"

temp=os.popen(com)
msg=temp.read()
index=string.find(msg,"<fullcount>")
index2=string.find(msg,"</fullcount>")
fc=int(msg[index+11:index2])

if fc==0:
   print "no"
else:
   print str(fc)
```

---

### Post by lvleph on 2008-01-05
I think I will have to make it so this script can handle symbols. It will take a bit of studying, because I don't know the address bar translations for all the symbols. And I don't know what it is called, and I don't remember how I figured out that @=%40.lol

EDIT: Okay, here are some of the codes. If this were perl I could write this up in a couple seconds, but I don't know python so I still have to study.
> 
"$"=%24
"&"=%26
"+"=%2B
","=%2C
"/"=%2F
":"=%3A
";"=%3B
"="=%3D
"?"=%3F
"@"=%40
The number after the percent are called hex code points. You can read about it [here](http://www.blooberry.com/indexdot/html/topics/urlencoding.htm).

---

### Post by lvleph on 2008-01-05
Can someone verify this loophole I have found in Gmail? It appears, when using ```
wget -O - https://"+username+":"+password+"@mail.google.com/mail/feed/atom --no-check-certificate
``` capitalization of characters does not matter. That is, one can log into there account even with incorrect capitalization. I have specifically tested it with replacing a capital with a lower case.

---

### Post by Goofy666 on 2008-01-06
I get a proper 401 when executing that command with chars of my password (de)capitalized. Maybe you should contact Google about it, if that really isn't the case with your info filled in =/.

@ RavUn; why are you using both gmail.py and gmail_subj.py? The latter is an extended gmail.py, if you want the functionality it offers you only need to use that script.

---

### Post by lvleph on 2008-01-06
Probably for the same reason I do, to get the number of new emails in a seperate color. I am going to rewrite the script again to take arguments so it outputs only the stuff you want. This way there is one script. Also, one could use awk to just out put the number.

---

### Post by lvleph on 2008-01-06
For those of you that were interested in my weather script. [Here it is.](http://ubuntuforums.org/showthread.php?t=660101)

---

### Post by shifty2 on 2008-01-06
I get this error:
```
adam@adam-laptop:~$ 
Conky: desktop window (e000d9) is subwindow of root window (52)
Conky: window type - override
Conky: drawing to created window (4400001)
Conky: drawing to double buffer
--00:02:35--  https://*****:*password*@mail.google.com/mail/feed/atom
           => `-'
Resolving mail.google.com... 66.249.91.18, 66.249.91.17, 66.249.91.83, ...
Connecting to mail.google.com|66.249.91.18|:443... failed: Connection refused.
Connecting to mail.google.com|66.249.91.17|:443... failed: Connection refused.
Connecting to mail.google.com|66.249.91.83|:443... failed: Connection refused.
Connecting to mail.google.com|66.249.91.19|:443... failed: Connection refused.
Traceback (most recent call last):
  File "/home/adam/.scripts/gmail.py", line 15, in <module>
    fc=int(msg[index+11:index2])
ValueError: invalid literal for int() with base 10: ''


```
I have to go through a proxy so I think this is what is causing the issue. I can copy and paste the URL into epiphany and access that page it is getting the info from but I cannot use the WGET command in the terminal on its own. Any ideas?

---

### Post by lvleph on 2008-01-06
The time I got those errors was when my username or password was wrong.

---

### Post by shifty2 on 2008-01-06
I may be being really slow here, it is late at night. This is what my gmail.py looks like (for [email]fred@googlemail.com[/email] with password fred)

```
import os
import string

#Enter your username and password below within double quotes
# eg. username="username" and password="password"
username="fred"
password="fred"

com="wget -O - https://"+username+":"+password+"@mail.google.com/mail/feed/atom --no-check-certificate"

temp=os.popen(com)
msg=temp.read()
index=string.find(msg,"<fullcount>")
index2=string.find(msg,"</fullcount>")
fc=int(msg[index+11:index2])

if fc==0:
   print "0 new"
else:
   print str(fc)+" new"
```

Is that correct? I am certain that I have typed in my username and password right so im not sure thats the issue here.

---

### Post by lvleph on 2008-01-06
Well I hope that is not your real info. Anyway, I think the problem might be that you have a googlemail account and not gmail account? Not sure if that is the problem, but it is the only thing I can think of.

---

### Post by shifty2 on 2008-01-07
Definitely a proxy issue as I have managed to get it all working properly when connecting at a different location with no proxy. I would have assumed that the script would have just used the global proxy settings? Interesting.

---

### Post by lvleph on 2008-01-07
That is interesting, and I have no idea how to fix that. I am thinking about rewriting the whole thing in bash using w3m to get the gmail stuff. That may solve the issue.

---

### Post by lvleph on 2008-01-07
I have been thinking about using w3m and realized that there might be too many issues using that method, so I don't know if I would want to takle it that way. I am going to keep thinking about the issue and see what I come up with.

EDIT: [Check this out if you are using a proxy.](http://wiki.archlinux.org/index.php/How_to_make_wget_to_work_with_proxy_and_proxy_authentification)

---

### Post by whayong on 2008-01-17
HI there.  Hopefully you guys still check this post.  I'm having problems getting this thing running in my Conky.  Here's the error:

Conky: desktop window (45) is root window
Conky: drawing to desktop window
Conky: drawing to double buffer
Traceback (most recent call last):
  File "/home/srx77/.scripts/gmail.py", line 9, in <module>
    com="wget -O - https://"+myusername+":"+mypassword+"@mail.google.com/mail/feed/atom --no-check-certificate"
NameError: name 'myusername' is not defined


Can anyone help?

---

### Post by staticvoid on 2008-01-17
what doe syour gmail.py file look like?
is your info correct?

sv

---

### Post by lvleph on 2008-01-17
> **whayong said:**
> HI there.  Hopefully you guys still check this post.  I'm having problems getting this thing running in my Conky.  Here's the error:

Conky: desktop window (45) is root window
Conky: drawing to desktop window
Conky: drawing to double buffer
Traceback (most recent call last):
  File "/home/srx77/.scripts/gmail.py", line 9, in <module>
    com="wget -O - https://"+myusername+":"+mypassword+"@mail.google.com/mail/feed/atom --no-check-certificate"
NameError: name 'myusername' is not defined


Can anyone help?

It looks like you didn't change the user name inside the code? Or you typed it incorrectly?

---

### Post by whayong on 2008-01-17
Ok, here's my gmail.py  (I changed the account info but everything else is typed accordingly)

```
import os
import string

#Enter your username and password below within double quotes
# eg. username="username" and password="password"
username="myusername"
password="mypassword"

com="wget -O - https://"+myusername+":"+mypassword+"@mail.google.com/mail/feed/atom --no-check-certificate"

temp=os.popen(com)
msg=temp.read()
index=string.find(msg,"<fullcount>")
index2=string.find(msg,"</fullcount>")
fc=int(msg[index+11:index2])

if fc==0:
   print "0 new"
else:
   print str(fc)+" new"
```

I saved it in ~/.scripts  QUESTION:  Am I supposed to have the "+" sign with my user name and password in this line? "com="wget -O - https://"+myusername+":"+mypassword+"@mail.google.com/mail/feed/atom --no-check-certificate""

and here is my .conkyrc

```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window no
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

maximum_width 500

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
#use_xft yes
xftfont Samanata
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color ace770

own_window_colour black
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10


#${color blue}FORTUNE ${hr 2}$color
#${execi 120 fortune -s | fold -w50}


#${color blue}LOGGING ${hr 2}$color
#${execi 30 tail -n3 /var/log/messages | fold -w50}



# stuff after 'TEXT' will be formatted on screen

TEXT

${color #5397d6}CPU ${hr 2}$color
${freq}MHz  
Load: ${loadavg}   
Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}

${color #5397d6}MEMORY / DISK ${hr 2}
$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Harddisk:
/	${fs_free_perc /}%	${fs_bar 6 /}$color
/home	${fs_free_perc /home}%	${fs_bar 6 /home}$color

${color #5397d6}Battery ${hr 2}$color
Battery: ${battery BAT1} 
${battery_bar BAT1}

${color #5397d6}GMail ${hr 2}
${color 95956B}${execi 300 python ~/.scripts/gmail.py} ${color FFFFFF}
```

Thanks for helping me out guys.  My first time last night using conky.

---

### Post by lvleph on 2008-01-17
It looks like you changed a line that shouldn't have been. The line you have as ```
com="wget -O - https://"+myusername+":"+mypassword+"@mail.google.com/mail/feed/atom --no-check-certificate"
```

Should look like ```
com="wget -O - https://"+username+":"+password+"@mail.google.com/mail/feed/atom --no-check-certificate"
```

---

### Post by whayong on 2008-01-17
Ahhhhhhhhhhhhhhhhhh, I think I get it now.  Give me a few minutes to turn the box on.  So what you're saying is I DO NOT change anything in this line?

```
com="wget -O - https://"+username+":"+password+"@mail.google.com/mail/feed/atom --no-check-certificate"
```

The way I understood it is I should change "+username+" to my gmail account name and "+password+" to my account password.  Alright let me give this a shot, let you know it a few.

Also, can anyone direct me to a "how to" for conky?  I need to get this thing auto started when I boot as well as change the colors.  I'm running this on Linux Mint Fluxbox.


edit: YUP!  That was it!  Everything works now.  Just have to mess with conky more and learn.  Thanks a lot for the help.  I appreciate it!

---

### Post by Smelly Avocado on 2008-01-17
any change of a screenie? 
i want to see if it's better than the other ones i've seen

---

### Post by staticvoid on 2008-01-18
a screenshot of the bar I use sort of flickers in metacity.  its basically one bar on the top of the screen.

sv

---

### Post by lvleph on 2008-01-18
Here is mine.

---

### Post by staticvoid on 2008-01-18
looks good! :D

---

### Post by kosak on 2008-01-22
does any of these scripts work with IMAP? It seems they are meant only for POP3 connections. :confused:

---

### Post by lvleph on 2008-01-22
The scrip described in this uses html, not pop or imap. Conky iteself can use either imap or pop3.

---

### Post by kosak on 2008-01-22
> **lvleph said:**
> The scrip described in this uses html, not pop or imap. Conky iteself can use either imap or pop3.

I read the variables page on sourceforge, but as you know conky is a bitch to config and would go around it if possible. 

So with this script i'll be able to get my emai notifications even if I have imap setup on gmail? 

thanks again!!

---

### Post by staticvoid on 2008-01-23
right, it basically makes an RSS feed of your emails and sends 'em to you.

:)

sv

---

### Post by lvleph on 2008-01-23
I fyou would like to see what it does type the following into terminal.
```
wget -O - https://<username>:<password>@mail.google.com/mail/feed/atom --no-check-certificate > ~/Desktop/gmail.html
```
Where <username> and <password> are your username and password, respectively. If you have symbols in your password you will have to use html escape codes for the symbol. I have posted that some where in this thread.

Open the gmail.html file that is now on your desktop and you will see a webpage with your current emails.

---

### Post by staticvoid on 2008-01-23
very cool. glad you posted that :)

simple.

exactly what its doing :)

sv

---

### Post by kosak on 2008-01-23
cool i'll try it later today! i'll post an image if all goes right~ (and code):lolflag:

---

### Post by staticvoid on 2008-01-23
it looks a little messy as an html page.. the python interprets it

---

### Post by lvleph on 2008-01-25
Anyone, elses gmail stop working? Mine is actually showing the xml code in the from field. Because of this I rewrote the code in perl. I will release in a different thread once I decide it is ready.

---

### Post by Choxo on 2008-01-27
let me now when you posted it!

---

### Post by lvleph on 2008-01-27
> **Choxo said:**
> let me now when you posted it!

I will post a link in here. I am working on some password issues, so that if there is a restricted symbol in the password the user doesn't need to worry about it and my script deals with it automagically. Also, working on displaying html escape codes correctly.

---

### Post by lvleph on 2008-01-27
[Here is my new gmail script.](http://ubuntuforums.org/showthread.php?p=4219577#post4219577)

---

### Post by staticvoid on 2008-01-28
looks great!!

---

### Post by RavUn on 2008-01-28
So, would it be possible to make the number of new emails a clickable link that opens up and loads gmail in firefox?

---

### Post by lvleph on 2008-01-28
As far as I know, no.

---

### Post by staticvoid on 2008-01-29
you could just ad a gmail link.

e.g.  [gmail]("http://www.gmail.com")

---

### Post by lvleph on 2008-01-29
but does conky allow links?

---

### Post by staticvoid on 2008-01-30
no clue... but it alowed a web address...

gtg.. boarding a plane :P

sv

---

### Post by kosak on 2008-01-30
Thanx lvleph! I went to your other link [http://ubuntuforums.org/showthread.php?p=4219577#post4219577]("http://ubuntuforums.org/showthread.php?p=4219577#post4219577") where you used the perl script.

to add the subject line replace on S & E cases:

print "From: $from[$i]\n\Subject: $subj[$i]\n";

:guitar:

Here's my pic!

---

### Post by roggo on 2008-01-31
To anyone that has been pondering about this...

This is my hack of this script to see different color for new emails, and other for 0 new emails. I dont know any other way to pass info to conky so I used basic I/O.

This is my first python script so just correct me if you have any ideas. :)

**Instructions:**

gedit /home/yourusername/scripts/conky-gmail-extended.py

Copy-paste this code into it.

New improved **conky-gmail-extended.py**:

```
import os
import string
import sys
import time

#Enter your username and password below within double quotes
# eg. username="username" and password="password"

username="username"
password="password"

filename="/home/yourusername/scripts/conky-gmail-new" #just change path, ie /home/yourusername/scripts/conky-gmail-new

emails=0
argument=sys.argv[1]

if (argument=="check"):

   com="wget -O - https://"+username+":"+password+"@mail.google.com/mail/feed/atom --no-check-certificate"
   temp=os.popen(com)
   msg=temp.read()
   index=string.find(msg,"<fullcount>")
   index2=string.find(msg,"</fullcount>")
   fc=int(msg[index+11:index2])

   if (int(fc)==0):
      if os.path.exists(filename):
         os.remove(filename)
   else:
      file = open(filename, "w")
      if (int(fc)==1):
         file.write("1 new email")
      else:
         file.write(str(fc)+" new emails")
      file.close

elif (argument=="read"):

   time.sleep(1)

   if os.path.exists(filename):
      file = open(filename, "r")
      emails = file.read()
      file.close()
   print emails
```

Close the file and

sudo chmod u+x /home/yourusername/scripts/conky-gmail-extended.py

Then slap this into **.conkyrc**:

```
Gmail: ${texeci 60 python /home/yourusername/scripts/conky-gmail-extended.py check}${if_existing /home/yourusername/scripts/conky-gmail-new}${color FF0000}${texeci 60 python /home/yourusername/scripts/conky-gmail-extended.py read} $else ${color FFFFFF}No new emails $endif
```

Hope this helps anyone! :)

EDIT:
Added instructions!

---

### Post by cyf3732 on 2008-01-31
Nice, but ...where is this file: [COLOR="Sienna"]**conky-gmail-new**[/COLOR] ?:confused:

> **roggo said:**
> To anyone that has been pondering about this...

This is my hack of this script to see different color for new emails, and other for 0 new emails. I dont know any other way to pass info to conky so I used basic I/O.

....

filename="/path/to/scripts/[COLOR="Sienna"]**conky-gmail-new**[/COLOR]" #used for I/O argument passing

....

```
Gmail: ${texeci 60 python /path/to/scripts/conky-gmail-extended.py check}${if_existing /path/to/scripts/[COLOR="Sienna"]**conky-gmail-new**[/COLOR]}${color FF0000}${texeci 60 python /path/to/scripts/conky-gmail-extended.py read} $else ${color FFFFFF}No new emails $endif
```
....

---

### Post by lvleph on 2008-01-31
I already posted the same solution. And you can use my script if you like, which is at the top of page 7.

---

### Post by roggo on 2008-01-31
> **cyf3732 said:**
> Nice, but ...where is this file: [COLOR="Sienna"]**conky-gmail-new**[/COLOR] ?:confused:

Where ever you put it. The script makes it, and then deletes it. As a signpost for "mails" or "no mails".

Ie. if you put the .py file to /home/yourusername/scripts/ you can also make the same path to the file. so it's /home/yourusername/scripts/conky-gmail-new

---

### Post by roggo on 2008-01-31
> **lvleph said:**
> I already posted the same solution. And you can use my script if you like, which is at the top of page 7.

Skimmed through your script and seemed way too intensive and redundant, so I made my own with the bare necessities. :)

Oh and your script only colors the number of the emails. Mine colors the whole thingie depending on mails or not.

---

### Post by cyf3732 on 2008-02-01
> **roggo said:**
> Where ever you put it. The script makes it, and then deletes it. As a signpost for "mails" or "no mails".

Ie. if you put the .py file to /home/yourusername/scripts/ you can also make the same path to the file. so it's /home/yourusername/scripts/conky-gmail-new

Many thanks mate! It works now! :guitar:
Why not consider providing these instructions in the first post above? :)

P.S. I found out that if you use [COLOR="DarkRed"]~/yourusrname/scripts/conky-gmail-new[/COLOR] it won't work, so be sure to change that setting to [COLOR="DarkRed"]/home/yourusername/scripts/conky-gmail-new[/COLOR], which roggo has said above.:)

Again, really thanks for hacking this script, roggo!!! :lolflag:

---

### Post by roggo on 2008-02-01
> **cyf3732 said:**
> Many thanks mate! It works now! :guitar:
Why not consider providing these instructions in the first post above? :)

P.S. I found out that if you use [COLOR="DarkRed"]~/yourusrname/scripts/conky-gmail-new[/COLOR] it won't work, so be sure to change that setting to [COLOR="DarkRed"]/home/yourusername/scripts/conky-gmail-new[/COLOR], which roggo has said above.:)

Again, really thanks for hacking this script, roggo!!! :lolflag:

Thanks! :)

Hope I can do something for the community sometime later as well... :popcorn:

---

### Post by cyf3732 on 2008-02-02
Wow, that's pretty nice roggo! Keep on nice work mate! :)

---

### Post by Palace_Chan on 2008-03-23
So the extended scripts to display subject etc....i cant get them to work
properly...they expand the conky to fill up  my entire screen when something
that they display gets too long! How can i avoid that ?

---

### Post by lvleph on 2008-03-23
The script I made uses text wrapping and so that shouldn't happen with mine. You can do a search for it; the title of the thread containing the script is Conky GMail Revisited.

---

### Post by ragingmon on 2008-05-20
Hi all I got this problem.

```
Traceback (most recent call last):
  File "/home/rage/.scripts/gmail_subj.py", line 47, in <module>
    print "From " + ff + ":\n" + message + "\"" # add the end " to the message
IOError: [Errno 32] Broken pipe

```

```
import os
import string

#Enter your username and password below within double quotes
# eg. username="username" and password="password"
username="username"
password="password"

com="wget -O - https://"+username+":"+password+"@mail.google.com/mail/feed/atom --no-check-certificate"

temp=os.popen(com)
msg=temp.read()
index=string.find(msg,"<fullcount>")
index2=string.find(msg,"</fullcount>")
fc=int(msg[index+11:index2])

if fc==0:
   print ""
else:
   # vars
   intChars = 35 # the number of characters displayed of long subjects
   intLimitedSubjects = 0 # 0,1 - disable,enable limiting of displayed subjects
   intSubjects = 2 # subjects to display if limiting of displayed subjects is enabled

   # open the output to read
   temp=os.popen(com)
   msg=temp.read()
   
   # find and display the subjects of the messages
   for i in range(1,fc+1): # run for every new email message
      # find...
      if i != 1: # delete part of the output that has been searched
         msg=msg[index2+17:]
      index=string.find(msg,"<entry><title>")
      index2=string.find(msg,"</title><summary>")
      fs=msg[index+14:index2]
      msg=msg[index2+15:]
      index=string.find(msg,"<author><name>")
      index2=string.find(msg,"</name><email>")
      ff=msg[index+14:index2]
      # these 3 rules are a modification of their original counterparts

      # display...
      message = "\"" + fs[:intChars] # display " and first 35 chars of subject
      if len(fs) > intChars:
         message += "..." # add '...' when subject is longer than 35 chars
      print "From " + ff + ":\n" + message + "\"" # add the end " to the message

      # Limiting of displayed subjects
      if intLimitedSubjects == 1:
         if i >= intSubjects:
            print str(intSubjects) + " out of " + str(fc) + " new messages shown."
            break
         else:
            continue
      else:
         continue
```

Here's a screenie: 
I tried both the sample in the first post and with my configuration.. That's why there's two outputs in here.
[IMG]http://img353.imageshack.us/img353/5453/screeniedj3.jpg[/IMG]

help please.. T_T

---

### Post by cpetercarter on 2008-05-21
I get the "broken pipe" error message too.

---

### Post by lvleph on 2008-05-21
> **lvleph said:**
> [Here is my new gmail script.](http://ubuntuforums.org/showthread.php?p=4219577#post4219577)

I will plug mine again, since it seems to be working for most people.

---

### Post by uzi09 on 2008-06-08
> **Choxo said:**
> Is there a possibility to define a fetch time?
How many times does this scripts updates itself?

Thanks!

you would edit the following line in .conkyrc (conky settings file)
```
${color}***@gmail.com: ${execi 60.0 python ~/.scripts/gmail.py}
```

the number after execi is after how many seconds you want it to update. Google recommends to check every 10 mins (I guess cuz they don't want to have their servers pinged for an update on e-mail every second by thousands of people).

As you can see, I've used 60.0 ie: 60 seconds (what? it's close enough to being 10 mins ;))

cheers

---

