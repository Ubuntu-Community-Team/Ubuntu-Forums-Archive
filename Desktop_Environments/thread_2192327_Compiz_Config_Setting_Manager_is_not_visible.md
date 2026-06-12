---
title: "Compiz Config Setting Manager is not visible"
date: 2013-12-07
forum: Desktop Environments
---

### Post by liyanagebg on 2013-12-07
Hello friends, I'm new to Ubuntu, and I'm usuing 13.10. I wanted to make desktop windows transperant and I tried to do it accordingly the instruction of this page ([http://zhixiangwu.blogspot.in/2013/02/making-my-ubuntu-look-prettier.html](http://zhixiangwu.blogspot.in/2013/02/making-my-ubuntu-look-prettier.html)). I followed its steps and when I clicked 'add' button to add values, application disappeared totally. After that when ever I start that program, upper panel bar and launcher indicate it is working, but I cannot see it. When I press 'Alt + F4' it is going away too. But it is not visible. I reinstalled several times using 'Software Center', nothing is happened. Please help me....

Instruction on that page is thus: 
[h=1][CENTER][COLOR=#333333][FONT=Arial]1) Click on the ‘Opacity Brightness & Saturation’ Plugin / ‘Opacity’ tab.[/FONT][/COLOR][/CENTER][/h]  2) Click ‘New’. Click ‘+’ and a new window will appear. Click ‘Grab’ and  then select the desktop window on which you want to enable  transparency. The name will then be filled into the Value field. Click  ‘add’. Range 0 (transparent) – 100 (opaque).
3) Transparency can the be changed via the Window Values slider .

---

### Post by monkeybrain20122 on 2013-12-07
Maybe because you have set opacity to 0 so it becomes invisible? I don't know which version of Ubuntu he is talking about, there is no slider in ccsm  in my 13.10.  [COLOR=#333333]Open CCSM , go to [FONT=Arial]Opacity Brightness & Saturation’ Plugin >  ‘Opacity[/FONT][/COLOR] > Windows Specific Settings, Choose your application in the list and click edit to change Window value to something between 0 to 100. 0 being totally transparent, 100 totally opaque.

---

### Post by liyanagebg on 2013-12-07
@[**[COLOR=#000000]monkeybrain20122[/COLOR]**]("http://ubuntuforums.org/member.php?u=1843403"), Your suggestion might be correct. But my friend, how can I open CCSM. I can do nothing with it, as it is invisible. Is there any other way or software by which I can open CCSM and do what you said. I tried 'terminal' too, same thing is happened. Is there any way to set all values of CCSM to default values by using terminal. Perhaps it might work, please....

---

### Post by deadflowr on 2013-12-07
I'm sure there is a gsettings command to do this, but my gsettings know how is for want.
So instead, install dconf-tools
```
sudo apt-get install dconf-tools
```
When it is installed open it and go to the section 
org > compiz > unity > plugins > obs
click it and a few lines in the main window will show.
look for the one with values, it should enclosed, and will probably look like this
(0,0)
cliuck on that line and you can then edit it, change the first number from zero to 100
and then hit enter.
the ccsm window should be opaque again.

---

### Post by liyanagebg on 2013-12-08
@[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar1276577_1.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=1276577") 				 				 					 						 	[**[COLOR=#000000]deadflowr[/COLOR]**]("http://ubuntuforums.org/member.php?u=1276577"), Thank you very much. It is working again perfectly. :popcorn:

---

### Post by cariboo on 2013-12-09
Moved to Desktop Environments, as this is a support question, and placing it here, may help others.

---

