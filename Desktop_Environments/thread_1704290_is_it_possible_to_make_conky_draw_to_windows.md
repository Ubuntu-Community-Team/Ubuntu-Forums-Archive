---
title: "is it possible to make conky draw to windows?"
date: 2011-03-10
forum: Desktop Environments
---

### Post by rkm.sbc on 2011-03-10
Hello folks, sorry if this isnt correct place to ask my question, forum seems large and im not familiar with it yet.  

I would like to draw to windows with conky. I allready have an idea with launching conky ~/. config1 & conky ~/.config2 and this should work but is it possible to have 2 conky windows without launching second instance of conky ?

---

### Post by stinkeye on 2011-03-10
Use ```
conky -c /path/to/your/conky
```
[**_[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")
You would need to start 2 instances of conky.

---

### Post by rkm.sbc on 2011-03-10
i am doing this, its not a problem to run conky with a specific config. But now im forced to launch conky twice to display the data i want to see in this way: 

[http://i51.tinypic.com/2wqwfw6.png](http://i51.tinypic.com/2wqwfw6.png)

So now im lanuching:
conky -c ~/conky-conf/conkyleft
conky -c ~/conky-conf/conkyright

Is it possible to get same effect within running only 1 instance of conky?

---

### Post by Copper Bezel on 2011-03-10
Make an executable text file with the two commands in it as a Conky startup script. That way, by adding to the script, you can run as many Conkies as you like with the one command.

---

### Post by rkm.sbc on 2011-03-10
You dont get me guys, i would like to avoid running two conkys. Cant some1 just answer like "possible" or "imopssible" ?:P

---

### Post by stinkeye on 2011-03-10
Possible.:roll:
Set the minimum width of your conky with the setting *(my resolution is 1680x1050)*
```
minimum_size 1680
``` 
and 

use the variable 
```
${alignr}
```
to move the content you want to the right hand side.
eg
```
$[time}${alignr}${uptime}
```


or use the variable 
${goto x}
where x is the horizontal pixel.
eg```
$[time}${goto 1600}${uptime}
```
This will line up better on the right hand side.

---

