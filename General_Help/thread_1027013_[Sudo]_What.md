---
title: "[Sudo] What?"
date: 2008-12-31
forum: General Help
---

### Post by lostfate on 2008-12-31
Today I just reinstalled ubuntu cause Windows is way to hard on my machine and upgraded to Ubuntu 8.10... I am wondering is there a way to clean my internet temp folder and other junk inside of my hard-drive? When I used Windows I had CCleaner do the work... but on Ubuntu idk where a drive cleaner would be or what, I scouted around a little and notice a code but this pops up when I try to type it in...

```
darkworld-games@dark-worldaa2:~$ sudo apt-get autoclean
[sudo] password for darkworld-games: 
```

It will not allow me to type my password in and it will not allow me to type anything in...

Please help me!, Thank you!

---

### Post by sovietdoughnut on 2008-12-31
even though nothing is appearing on the screen, the terminal is still accepting input. it just doesn't display arbitrary characters, for the sake of concealing your password's length i suppose. that should answer that question, but what exactly is your concern for doing this?

---

### Post by lostfate on 2008-12-31
Why I am doing is for PTC offers such as Cashlagoon's and Bux.to like I did with windows, so it doesn't show my password but it will accept it when I press enter, right?

Edit; Ahhh it worked, It confused me badly

But I can still do paid to click offers can't I?

---

### Post by dragos240 on 2008-12-31
type your login password for sudo.

---

### Post by 2hot6ft2 on 2008-12-31
> **lostfate said:**
> I am wondering is there a way to clean my internet temp folder and other junk inside of my hard-drive? When I used Windows I had CCleaner do the work... but on Ubuntu idk where a drive cleaner would be or what
For future reference this has a nice cleanup feature [http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11)
Also if you run

```
sudo apt-get autoremove

```
it will clear out some packages that are no longer needed.

In System>Administration>Synaptic Package Manager you can search for the following and instaal to use them

Localepurge - purges language files for things you don't speak or anticipate speaking.

GtkOrphan- removes orphaned files, frees disk space
INSTEAD... You could just install deborphan and create a new filter in Synaptics:

Settings > Filters > New and uncheck all boxes except 'Orphaned'. You'll now have a new category in the Custom tab that does the same as gtkorphan.

---

### Post by lostfate on 2008-12-31
lol I do not get any of that mumbo jumbo because I am not good with code at all, in the long run all it does is cause me a massive headache, but btw I have a Java application and I do not have one clue on how to run it, please help me with it, thanks!

---

### Post by 2hot6ft2 on 2008-12-31
I believe the default setting for Firefox is to clear internet files every so often. I know I have seen mine do it without any input on my part. You could always change the setting by going to Edit>Preferences in Firefox

---

### Post by lostfate on 2008-12-31
I need help on running a java application and in the terminal I enabled Restricted Areas but it brought up something that I do not have a single clue about getting apast....


```
Package configuration

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring sun-java6-jre &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474;     under the control of your Operating System and designing,             &#8593; 
 &#9474;     developing and testing Programs to be run under the control of your   &#9618; 
 &#9474;     Operating System; (c) you do not combine, configure or distribute     &#9618; 
 &#9474;     the Software to run in conjunction with any additional software       &#9646; 
 &#9474;     that implements the same or similar functionality or APIs as the      &#9618; 
 &#9474;     Software; (d) you do not remove or modify any included license        &#9618; 
 &#9474;     agreement or impede or prevent it from displaying and requiring       &#9618; 
 &#9474;     acceptance; (e) you only distribute the Software subject to this      &#9618; 
 &#9474;     license agreement; and (f) you agree to defend and indemnify Sun      &#9618; 
 &#9474;     and its licensors from and against any damages, costs, liabilities,   &#9618; 
 &#9474;     settlement amounts and/or expenses (including attorneys' fees)        &#9618; 
 &#9474;     incurred in connection with any claim, lawsuit or action by any       &#9618; 
 &#9474;     third party that arises or results from (i) the use or distribution   &#9618; 
 &#9474;     of your Operating System, or any part thereof, in any manner, or      &#8595; 
 &#9474;                                                                             
 &#9474;                                  <Ok>                                       
 &#9474;                                                                           &#9474; 
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```


Edit: I have typed in everything...

---

### Post by 2hot6ft2 on 2008-12-31
> **lostfate said:**
> lol I do not get any of that mumbo jumbo because I am not good with code at all, in the long run all it does is cause me a massive headache, but btw I have a [COLOR="Blue"]Java[/COLOR] application and I do not have one clue on how to run it, please help me with it, thanks!
You need to put this in a terminal and hit Enter
Applications>Accessories>Terminal
```
sudo apt-get install ubuntu-restricted-extras
```
When the agreement gets to where you have to accept it....hit the Tab button on your keyboard then hit the Enter Button.

---

### Post by 2hot6ft2 on 2008-12-31
> **lostfate said:**
> I need help on running a java application and in the terminal I enabled Restricted Areas but it brought up something that I do not have a single clue about getting apast....


```
Package configuration

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring sun-java6-jre &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474;     under the control of your Operating System and designing,             &#8593; 
 &#9474;     developing and testing Programs to be run under the control of your   &#9618; 
 &#9474;     Operating System; (c) you do not combine, configure or distribute     &#9618; 
 &#9474;     the Software to run in conjunction with any additional software       &#9646; 
 &#9474;     that implements the same or similar functionality or APIs as the      &#9618; 
 &#9474;     Software; (d) you do not remove or modify any included license        &#9618; 
 &#9474;     agreement or impede or prevent it from displaying and requiring       &#9618; 
 &#9474;     acceptance; (e) you only distribute the Software subject to this      &#9618; 
 &#9474;     license agreement; and (f) you agree to defend and indemnify Sun      &#9618; 
 &#9474;     and its licensors from and against any damages, costs, liabilities,   &#9618; 
 &#9474;     settlement amounts and/or expenses (including attorneys' fees)        &#9618; 
 &#9474;     incurred in connection with any claim, lawsuit or action by any       &#9618; 
 &#9474;     third party that arises or results from (i) the use or distribution   &#9618; 
 &#9474;     of your Operating System, or any part thereof, in any manner, or      &#8595; 
 &#9474;                                                                             
 &#9474;                                  <Ok>                                       
 &#9474;                                                                           &#9474; 
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;
```


Edit: I have typed in everything...
hit the Tab button on your keyboard then hit the Enter Button.

---

