---
title: "How do I input Chinese?"
date: 2006-08-20
forum: Desktop Environments
---

### Post by NooBeee on 2006-08-20
I have a really simple question: How do I use a Chinese keyboard layout in Ubuntu? It's not listed in the keyboard layouts.

---

### Post by NooBeee on 2006-08-25
Anyone??

psh...come on, this is something even Win XP can do.....

---

### Post by nk_joe on 2006-08-25
[http://www.ubuntuforums.org/archive/index.php/t-25513.html](http://www.ubuntuforums.org/archive/index.php/t-25513.html)

may be helpful to u .... ;)

---

### Post by NooBeee on 2006-08-26
Thanks, I'll check it out.....but this is the reason why people have a hard time switching to linux

---

### Post by fdimmling on 2006-08-26
In the meantime Chinese language support is quite easy in Ubuntu. AFAIK you just install language-support-zh and you get your Chinese input and many more things. All you need is to switch the language environment for the program in question before starting it - if you normally run a non-Chinese locale.

To input Chinese in a document using gedit you type

export LANG=zh_CN.UTF-8
gedit

Activate Chinese input by pressing Ctrl-Space and you can enter Chinese in your document.

Friedrich

---

### Post by NooBeee on 2006-08-31
Changing the locale (export LANG=zh_CH.utf-8) isn't working for me. I can change the language before i log in though, and that works. However, everything (menus, buttons, etc) is in chinese. I just want to be able to input it, i don't want to see it everywhere [-X 

Also, what is SCIM and how will it help me?





If only Ubuntu had a normal chinese keyboard layout like windows.....

---

### Post by dyoung66 on 2006-08-31
Scim(Gnome) or Skim(KDE) is a Smart Common Input Method (SCIM).
Try their website.
google: scim 
=> [http://www.scim-im.org/](http://www.scim-im.org/)
they've got lots of info and screenshots.
In a nutshell:
scim/skim will put an icon in your system tray that will let you change your input text from english to chinese or japanese or many others (i can only write some japanese.) you can activate it with a keyboard shortcut, a right-click context menu or from the system tray.(all customisable)
For japanese you type in romaji(english spelling of japanese words) and it converts to kana/kanji.
Works the same way for Chinese.
eg:
nihongo => &#26085;&#26412;&#35486;.

hope this helps.

---

### Post by tilai on 2006-09-01
From the [archive]("http://www.ubuntuforums.org/archive/index.php/t-25513.html")  I would like to be able to use pinyin input in office programs among others, but what kind of file is .xsession? How do I create it?

> If you cant SCIM to work in every application you need to create a file called .xsession in your home with the following text :

export XMODIFIERS=@im=scim
export GTK_IM_MODULE=scim
gnome-session

---

### Post by Blur-king on 2006-09-01
Hi I use the instruction below to activate SCIM and it allows me to use pinyin. see this thread if needed
[http://www.ubuntuforums.org/showthread.php?t=208623](http://www.ubuntuforums.org/showthread.php?t=208623)
     


    



Quick setup  ***SCIM** is the name of the program that will allow you to input a CJK language in Ubuntu 6.06 Dapper Drake.* [LIST=1]
[*]Open system System>Administration>Language Support[1]("https://help.ubuntu.com/community/SCIM?highlight=%28scim%29#fndef-ee9899586ba56e1813c3cf94dfa94c61f3296271-0"):[/LIST][LIST]
[*][IMG]https://help.ubuntu.com/community/SCIM?action=AttachFile&do=get&target=Menus.jpg[/IMG][/LIST][LIST=1]
[*]and install the support package corresponding to the language you want to input[2]("https://help.ubuntu.com/community/SCIM?highlight=%28scim%29#fndef-adac221a6fc0e5ff7b3fc2457120b79733a8936b-1"):[/LIST][LIST]
[*][IMG]https://help.ubuntu.com/community/SCIM?action=AttachFile&do=get&target=Screenshot-Language_Support.png[/IMG][/LIST][LIST=1]
[*]then log out (System>Quit>Log Out), and login again.[/LIST]If your session is using a CJK language (for example, all you menus are in Chinese, Japanese or Korean) you should be able to input it in any application (go to [Using **SCIM**]("https://help.ubuntu.com/community/SCIM?highlight=%28scim%29#Using") to learn how to do it). 
  **Additionnal configuration if you're not using a CJK session**

  **Note :** *You should already be able to use **SCIM** input in a few applications, like gedit (Application>Accessories>Text Editor), by right clicking on the document, then selecting Input Methods>**SCIM** Input Method. However, it won't work in the others, like Open Office.* 
 The recommended method to set up **SCIM** input for all applications is using a command-line tool called im-switch (where im stands for Input Method, obviously [IMG]https://help.ubuntu.com/htdocs/ubuntu/img/smile.png[/IMG] ). Before that, you will have to know the name of the locale you're using. In a terminal (Applications>Accessories>Terminal) type : 
 locale | grep LANG= The anwer would be something like   
 LANG=en_GB.UTF-8   where the relevant part is en_GB (en standing for English and GB for the country, here Great Britain). Another example could be fr_FR (fr for French and FR for France).
 Now you just have to tell the system you want to use **SCIM** as the input method for your locale, using   
 im-switch -z “your locale” -s **scim**   In the above example, with an en_GB locale, you would type in the terminal : 
 im-switch -z en_GB -s **scim**  
 Log out, then log in again. **SCIM** should be now the default input for all applications (go to [Using **SCIM**]("https://help.ubuntu.com/community/SCIM?highlight=%28scim%29#Using") to learn how to use it) 
 **Note for Xubuntu users :** On Xubuntu, the system will ask you first to install the package libapt-pkg-perl. Install it from Synaptic (see above) or by the command line : [LIST]
[*] sudo apt-get install libapt-pkg-perl[/LIST]Then you'll be ready to use im-switch (see just above). In Xubuntu, you will also have to apply the following instructions : 
  **In case all of this doesn't work**

  You might have to add your locale as a supported locale, by editing (you might have to create it) the file  ~/.**scim**/global (the ~ means it's in your home directory, the . that .**scim** directory is a hidden file. Just type in a terminal :  
 gedit ~/.**scim**/global   
 If you can find a line like    
 /SupportedUnicodeLocales = en_US.UTF-8  add your locale to it after a coma, not forgetting you need to add the full name reported by locale | grep LANG= after LANG= . In case of English for Great Britain, your line would look like this one :  
 /SupportedUnicodeLocales = en_US.UTF-8,en_GB.UTF-8  If the line wasn't there, create it, then save the file. 
 Log out, then log in and you should be able to use **SCIM** input in every application.  
   
  **Using [B]SCIM**[/B]

  **SCIM** should now start along with every application. To trigger it, use any of these shortcut keys : Control+space, Shift+space, Zenkaku_Hankaku(on Japanese keyboard), Hangul(on Korean keyboard) 
 While inputting, if you want to switch back and forth between your CJK language and your session language, you can just use the Shift key. Fast and easy!

---

### Post by NooBeee on 2006-09-01
Thanks everyone, very helpful information. Personally, I think Ubuntu should just help you set up SCIM in the install, considering how useful it seems to be.

UPDATE:

I've tried the commands (im-switch, etc) but ctrl space does nothing. I tried adding sudo to the command but i get "No alternatives defined for language en_US.UTF-8"
](*,) ](*,) ](*,) ](*,)

---

### Post by NooBeee on 2006-09-01
> **NooBeee said:**
> Thanks everyone, very helpful information. Personally, I think Ubuntu should just help you set up SCIM in the install, considering how useful it seems to be.

UPDATE:
I'm using Ubuntu, but the system still said "Warning: dependency check won't work because libapt-pkg-perl isn't installed."

---

### Post by tilai on 2006-09-02
[http://www.ubuntuforums.org/showthread.php?t=208623]("http://www.ubuntuforums.org/showthread.php?t=208623")> **NooBeee said:**
> UPDATE:
I'm using Ubuntu, but the system still said "Warning: dependency check won't work because libapt-pkg-perl isn't installed."

Did you follow BlurKing's instructions completely?
> Note : Note for Xubuntu users : On Xubuntu, the system will ask you first to install the package libapt-pkg-perl. Install it from Synaptic (see above) or by the command line :
sudo apt-get install libapt-pkg-perl
Then you'll be ready to use im-switch (see just above). In Xubuntu, you will also have to apply the following instructions : 

I followed her(?) instructions and now have scim operating, although I have at least one program (aMSN)where I still can't input in pinyin. Probably a problem with aMSN itself. I'm going to check the aMSN thing elsewhere.

Edit: I know it's said Xubuntu, but works for my Ubuntu. I actually followed BlurKing's post in [there]("http://www.ubuntuforums.org/showthread.php?t=208623").
> Follow the instruction in the docs, it will prompt you that you need " libapt-pkg-perl " , just sudo aptitude install it and repeat the im command again, now it will promt you to install " scim-qtimm " , sudo aptitude install this and run the im switch command again. Then logout and relogin. The scim icon should in the panel. You can then fine tune your setup by clicking on the icon. And yes I think there may not be a need to reconfigure Open Office as mention in my earlier post. Remember that you need to logout and then login before you can see any changes to the SCIM. 

---

### Post by NooBeee on 2006-09-09
> **NooBeee said:**
> Thanks everyone, very helpful information. Personally, I think Ubuntu should just help you set up SCIM in the install, considering how useful it seems to be.

UPDATE:

I've tried the commands (im-switch, etc) but ctrl space does nothing. I tried adding sudo to the command but i get "No alternatives defined for language en_US.UTF-8"
](*,) ](*,) ](*,) ](*,)

Somehow i double posted...odd...
This is the message i wanted to post. (Yes the problem still exists.)

---

### Post by shirilover on 2006-09-09
I followed the instructions located here -> [http://www.mrbass.org/linux/ubuntu/scim/]("http://www.mrbass.org/linux/ubuntu/scim/")

It worked very well.

---

### Post by NooBeee on 2006-09-11
I can't seem to use SCIM....
Where does it go??

---

### Post by the lush on 2006-09-19
I used these instructions [https://help.ubuntu.com/community/SCIM]("https://help.ubuntu.com/community/SCIM"), and they seem to work. I got the error where the system will ask you first to install the package libapt-pkg-perl, which should only happen with Xubuntu, but I am using Ubuntu. I followed the instructions to fix the problem under Xubuntu and they worked perfectly.

After restarting, you should see a wee icon in the system tray near the clock. Right click onit and you will find Scim set-up.
N.B. For some odd reason the first time it runs after you have re-booted it takes a long time to appear/start working (I thought it had a problem at first when I tried it in Firefox), but it does get there in the end. Subsequent boots do not display this problem.

It does not appear to allow you to use Hanyu Pinyin to input traditional characters though. I am still trying to find a solution to this problem, so if anyone knows the answer please let me know.

---

### Post by benjaminzsj on 2006-09-19
NooBeee, if you can read Chinese, you better check out [here]("http://forum.ubuntu.org.cn/forum-8.html&sid=00ff3cb3d307ee7ab8b8f6703a15683b"). Or disappointedly you can't get ultimate solution both forums, maybe I can translate it to you.

To the lush: I guess there's a toggle on the scim panel to let you switch between simplified and traditional.

---

### Post by tilai on 2006-09-19
> **benjaminzsj said:**
> NooBeee, if you can read Chinese, you better check out [here]("http://forum.ubuntu.org.cn/forum-8.html&sid=00ff3cb3d307ee7ab8b8f6703a15683b"). Or disappointedly you can't get ultimate solution both forums, maybe I can translate it to you.

To the lush: I guess there's a toggle on the scim panel to let you switch between simplified and traditional.

Er.. a bit strange. The page doesn't seem to be loading. And I am in China.:rolleyes:

---

### Post by the lush on 2006-09-29
> **benjaminzsj said:**
> NooBeee, if you can read Chinese, you better check out [here]("http://forum.ubuntu.org.cn/forum-8.html&sid=00ff3cb3d307ee7ab8b8f6703a15683b"). Or disappointedly you can't get ultimate solution both forums, maybe I can translate it to you.

To the lush: I guess there's a toggle on the scim panel to let you switch between simplified and traditional.

There is, but it does not allow the use of Pinyin with traditional characters. The closest I can get is to use chewing, with the keyboard layout set to Hanyu Pinyin, but I don't really understand the chewing IME. Does anyone know where I can find some good instructions for it? My searches have been fruitless.

Regarding a point made by NooBeee earlier, I agree, during the set-up of Ubuntu it should ask if you would like to be able to use alternative input methods with your chosen locale, to save messing about with the terminal later.

---

### Post by darsu on 2006-09-29
Does anyone know of a Chinese character browser which supports radical lookup? Sure, there are web sites which do, but I could use an offline tool.

---

### Post by ClarkePeters on 2006-09-29
If you can type in Chinese then obviously you know Chinese. Why not just change language temporarily at login? You can then input in chinese and  still input English, English web pages and English documents still show up in English. What's wrong with having your Applications, and menu bars etc in Chinese temporarily?   alt + ctl + backspace to get back to English is a snap.

---

### Post by rykel on 2006-12-24
Thank you VERY MUCH!!

This is THE thread I have been looking for, because, ever since I switched to Edgy, I have not been able to even get SCIM to autostart on bootup... but now, it is finally working...

---

### Post by the lush on 2007-04-25
> **darsu said:**
> Does anyone know of a Chinese character browser which supports radical lookup? Sure, there are web sites which do, but I could use an offline tool.
If you need an offline character browser/dictionary/translator and a whole lot of other tasty stuff, go to [http://www.mandarintools.com/]("http://www.mandarintools.com/"). Find and download something called DimSum, it is a Java application and works perfectly under Linux (and Windows). I find it indispensible.

---

### Post by gugachiu on 2007-12-27
so no one found a solution to typing traditional characters using pinyin?

---

