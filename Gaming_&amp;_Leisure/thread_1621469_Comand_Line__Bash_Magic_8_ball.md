---
title: "Comand Line / Bash Magic 8 ball?"
date: 2010-11-14
forum: Gaming &amp; Leisure
---

### Post by RabbitWho on 2010-11-14
I feel sure one of these existed... 

I guess it's a program that ignores whatever your input is and gives you  back one of maybe 4/8/16 (?) answers seemingly at random every time it  gets any command at all. 
Did I dream it?

---

### Post by HoKaze on 2010-11-14
Ran a quick search myself, most of the top results are for GUI versions, and in particular the magic 8 ball screenlet. Either way if it's just a simple program that displays one of so many random messages with no regard to the actual input (and assuming it has no extra options to pass to it when executed) then it should be fairly easy to write in bash or python.
If I remember tomorrow I might quickly throw something together along those lines, probably using python.

Edit: Nevermind, quickly wrote up something in two minutes, hope this is sort of what you want? (Requires python 2.6)

---

### Post by sisco311 on 2010-11-14
Hmmm, I bored. So here is a bash/fortune variant. You need to install fortune first, then create the fortune file,  /usr/share/games/fortunes/magic8ball:
```
As I see it, yes
%
It is certain
%
It is decidedly so
%
Most likely
%
Outlook good
%
Signs point to yes
%
Without a doubt
%
Yes
%
Yes - definitely
%
You may rely on it
%
Reply hazy, try again
%
Ask again later
%
Better not tell you now
%
Cannot predict now
%
Concentrate and ask again
%
Don't count on it
%
My reply is no
%
My sources say no
%
Outlook not so good
%
Very doubtful
%

```
create the random access file:
```
sudo strfile /usr/share/games/fortunes/magic8ball
```
and run:
```
read -p "What's your question?"$'\n' && fortune magic8ball
```

---

### Post by Vrroom on 2010-11-15
Nice simple script to have some command line fun. One problem: The terminal crashes if I launch the script from a custom launcher after I type the question and hit enter. Though the script works fine if I do ./magic8ball from terminal.

---

### Post by HoKaze on 2010-11-15
> **Vrroom said:**
> Nice simple script to have some command line fun. One problem: The terminal crashes if I launch the script from a custom launcher after I type the question and hit enter. Though the script works fine if I do ./magic8ball from terminal.
I'm pretty sure most launchers will run a program in the terminal and then close the terminal as soon as the program finishes. In other words, it'll print the response but close the terminal before you can actually even see the response. The way to avoid this is to either run it manually from the command line, add a pause onto the end of the script or request additional user input to close the script after the message has been displayed.
(This applies to both the python script and the fortune method)

Fix for python version:
Add this code to the end of the file if you want to have to press enter to continue
```
raw_input()
```or add this to pause for 2 seconds:
```
import time
time.sleep(2)
```Fix for bash/fortune method:
Instead of using this command,
```
read -p "What's your question?"$'\n' && fortune magic8ball
```Use this command instead:
```
read -p "What's your question?"$'\n' && fortune magic8ball && sleep 2
```

---

### Post by Vrroom on 2010-11-16
> **HoKaze said:**
> I'm pretty sure most launchers will run a program in the terminal and then close the terminal as soon as the program finishes. In other words, it'll print the response but close the terminal before you can actually even see the response. The way to avoid this is to either run it manually from the command line, add a pause onto the end of the script or request additional user input to close the script after the message has been displayed.
(This applies to both the python script and the fortune method)

Fix for python version:
Add this code to the end of the file if you want to have to press enter to continue
```
raw_input()
```or add this to pause for 2 seconds:
```
import time
time.sleep(2)
```Fix for bash/fortune method:
Instead of using this command,
```
read -p "What's your question?"$'\n' && fortune magic8ball
```Use this command instead:
```
read -p "What's your question?"$'\n' && fortune magic8ball && sleep 2
```

Great work. Thanks alot :)

---

### Post by Vrroom on 2010-11-16
One more question. Is it possible to loop entire thing after raw_input()? I mean after I hit enter I am again brought to the line 'what is your question' The only way to close terminal would be from window controls. Sorry I am no programmer and i have no idea how to do this :)

---

### Post by sisco311 on 2010-11-16
```
while (True):
  raw_input("What is your question?\n")
  print random.choice(answers) + '\n'

```

```
while true; do read -p "What's your question?"$'\n' && fortune magic8ball; echo; done
```

---

### Post by Vrroom on 2010-11-16
Nice. Thanks alot :)

---

### Post by Vrroom on 2010-11-16
I have combined everything form your scripts and added standard answers from wikipedia :)

```
#!/usr/bin/env python
# Magic 8 ball program

import random
answers = ["As I see it, yes","It is certain","It is decidedly so","Most likely","Outlook good","Signs point to yes","Without a doubt","Yes","Yes definitely","You may rely on it","Reply hazy, try again","Ask again later","Better not tell you now","Cannot predict now","Concentrate and ask again","Don't count on it","My reply is no","My sources say no","Outlook not so good","Very doubtful"]
raw_input("What is your question?\n")
response = random.choice(answers)
print response + '\n'
while (True):
  raw_input("What is your question?\n")
  print random.choice(answers) + '\n'
```

---

### Post by RabbitWho on 2010-12-22
Hi everyone! 

Sorry it took me so long to reply.. this is so cool! Thank you! 

What is your question?
Am I a cat?
Without a doubt

What is your question?
Will my flight be cancelled tomorrow?
Concentrate and ask again

What is your question?
Will my flight be cancelled tomorrow?
As I see it, yes


Drat! :D ;)

---

