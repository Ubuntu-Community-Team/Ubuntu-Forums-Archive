---
title: "Japanese Input in english session - Firefox? Need Help."
date: 2006-06-06
forum: Desktop Environments
---

### Post by mogliii on 2006-06-06
Hi,

I have [X,K]ubuntu 6.06 installed on my IBM T40. As I spend my time in Japan at the moment, I am really interested in writing in japanese. To be honest its the only reason why I didnt switch my daily surfing and emailing to linux.

With ubuntu 5.10 I never succeeded to input in any other aplication than Synaptic.

With the new 6.06 I was happy to hear, that scim would be installed automatically. I hoped this issue would be solved.

But until now, 3 long evenings searching the web, it still doesnt work as I would like it.

Only in Synaptic I am able to input japanese, and it works really fine. But unfortunately I dont need it there.

So after my searches in the internet I didnt not stumble over any information that stated, that japanese input in an english ubuntu will work in english Firefox (Thunderbird) in Dapper. (Many posts are from last year, and I guess that with dapper these articles are obsolete)

Can anyone prove me wrong please?

===========
Guess my proplem applies to < 1% of users :-(

---

### Post by gemgem on 2006-06-06
i actually [just asked this question]("http://www.ubuntuforums.org/showthread.php?t=188853") a couple of days ago. but i wanted to input  chinese traditional instead of japanese in english session.

first, _make sure that all the japanese input thingies for scim are installed_. 
for chinese traditional it's scim-chewing. i don't know what it is for japanese. scim-anthy i think... i remember seeing it mentioned as i was searching the web for how to input chinese. so look at synaptic and see if it's there already.

if it is, go to this page and follow the steps outlined there: [https://wiki.ubuntu.com/InputMethods/SCIM/CJK_Chinese_Japanese_Korean_Input_Method_configuration_using_SCIM_in_Ubuntu_6%2e06_Dapper_Drake]("https://wiki.ubuntu.com/InputMethods/SCIM/CJK_Chinese_Japanese_Korean_Input_Method_configuration_using_SCIM_in_Ubuntu_6%2e06_Dapper_Drake")

----

it should be ok right off the bat (supposedly).

[COLOR="DarkGreen"]but if it doesn't work right away, like it did in my case, do these things:[/COLOR]

my first problem was that the command "im-switch" (as mentioned [in the link i gave above]("https://wiki.ubuntu.com/InputMethods/SCIM/CJK_Chinese_Japanese_Korean_Input_Method_configuration_using_SCIM_in_Ubuntu_6%2e06_Dapper_Drake")) was "not found" when i typed it in terminal.

**i found online that you're supposed to do have "im-switch" INSTALLED first to be able to use this command. so look for it in synaptic. if you can't find "im-switch" in synaptic, go to the repositories list and check everything in the little boxes. **

and then type 

**im-switch -z zh_tw -s scim**

**but change zh_tw to whatever the code is for japanese**. maybe jp_japan or something that looks like that. zh_tw is "chinese traditional for taiwan".

after you type that, you'll also have to type

**im-switch -s scim_xim -z default**

[COLOR="DarkGreen"]typing the code i mentioned above will make scim the default input method for everything, firefox, text editor, gaim, etc.. etc.. you won't have to right click and "select input method" and then choose scim anymore.[/COLOR]

after doing these things, l[COLOR="DarkGreen"]og out and log in again,[/COLOR] and these changes will take effect.

ctrl-space to switch layouts.

there will be a little box that will show the different input methods you have installed. you can click it and see options, etc..

------

i hope i'm able to help. i'm not a super expert user so if you encounter problems outside the scope of what i mentioned here, i might be unable to help. :D

---

### Post by mogliii on 2006-06-06
Thx for your answer. Gives me hope that I'm not the only one out there with that problem :-)

I followed your guide.

im-switch was installed. 

I also followed the instructions on the ubuntu wiki. When typing those commands, I dont get any error messages.

But still, japanese input only works in synaptic. 

But one question to you, so I have it black on white:
You have english Ubuntu installed, and you are able to input Chinese in Firefox (from the Ubuntu-Repos) and Thunderbird, and Openoffice...

I'm not sure what else i should do... 

Here my im-switch -l output

```
 im-switch -l
You have en_GB setup in "/home/*****/.xinput.d".
=======================================================
No alternatives defined for language en_GB
=======================================================
The following languages have been configured to use input methods:
en_GB ja_JP ko_KR zh_CN zh_TW

```

I also attached as picture, how it looks in synaptic. I guess this is the way it should work in all applications

---

### Post by Rondonjin on 2006-06-06
[QUOTE=mogliii]Hi,

I have [X,K]ubuntu 6.06 installed on my IBM T40. As I spend my time in Japan at the moment, I am really interested in writing in japanese. To be honest its the only reason why I didnt switch my daily surfing and emailing to linux.

With ubuntu 5.10 I never succeeded to input in any other aplication than Synaptic.

With the new 6.06 I was happy to hear, that scim would be installed automatically. I hoped this issue would be solved.

But until now, 3 long evenings searching the web, it still doesnt work as I would like it.

Only in Synaptic I am able to input japanese, and it works really fine. But unfortunately I dont need it there.

So after my searches in the internet I didnt not stumble over any information that stated, that japanese input in an english ubuntu will work in english Firefox (Thunderbird) in Dapper. (Many posts are from last year, and I guess that with dapper these articles are obsolete)

Can anyone prove me wrong please?

===========
Guess my proplem applies to < 1% of users :-([/QUOTE]

I don't know what to tell you. I use an English (UK) system (Timezone Japan, keyboard US) and SCIM works fine for me. I've never used this im-switch thingie you've mentioned in another post, not sure what it's for even after reading the info. Do you have a keyboard icon on your Gnome panel?

I also have 3 hidden directories in my home: .anthy, .scim and .xinput.d

Wayne

---

### Post by gemgem on 2006-06-06
mogliii, did you type this "im-switch -s scim_xim -z default"? this advice was given to me when i previously asked about inputting traditional chinese characters. 

supposedly "[COLOR="DarkGreen"]im-switch -s scim_xim -z default[/COLOR]" would make scim become the default input method for _all programs_ (and not only certain ones). 

remember to log out and log in again.

---

### Post by rlgc79 on 2006-06-06
Following this link [https://wiki.ubuntu.com/JapaneseInputHowToInBreezy?highlight=%28japanese%29](https://wiki.ubuntu.com/JapaneseInputHowToInBreezy?highlight=%28japanese%29)

I can type in Japanese.. No problems at all.. (Dapper)
Don't forget to install everything related to  Japanese fonts in synaptic.

Cheers

---

### Post by mogliii on 2006-06-06
Hi,

will try as soon as I have some free time. If I get it working, I will post here.

But one thing came into my mind... maybe its due to [G,K,X]ubuntu?

I installed with an Kubuntu CD, and installed Xubuntu-Desktop later. And now i'm trying to get it working in Xubuntu.

What about you two? Are you using Gubuntu? 
(Sorry for writing Gubuntu (Gnome+Ubuntu), but its always a little confusing for me when someone says: works in ubuntu dapper, cause I cannot distinguish if it is Gnome+ubuntu or the ubuntu-base)

But I got new hope ;-)

---

### Post by Rondonjin on 2006-06-07
[QUOTE=mogliii]Thx for your answer. Gives me hope that I'm not the only one out there with that problem :-)

I followed your guide.

im-switch was installed. 

I also followed the instructions on the ubuntu wiki. When typing those commands, I dont get any error messages.

But still, japanese input only works in synaptic. 

But one question to you, so I have it black on white:
You have english Ubuntu installed, and you are able to input Chinese in Firefox (from the Ubuntu-Repos) and Thunderbird, and Openoffice...

I'm not sure what else i should do... 

Here my im-switch -l output

```
 im-switch -l
You have en_GB setup in "/home/*****/.xinput.d".
=======================================================
No alternatives defined for language en_GB
=======================================================
The following languages have been configured to use input methods:
en_GB ja_JP ko_KR zh_CN zh_TW

```

I also attached as picture, how it looks in synaptic. I guess this is the way it should work in all applications[/QUOTE]

Quite a few languages set up there! :-)

wayne@Merlin:~$ im-switch -l
No alternatives defined for language en_GB
=======================================================
The following languages have been configured to use input methods:
ja_JP

Wayne

---

### Post by mogliii on 2006-06-07
&#12424;&#12363;&#12387;&#12383;&#65281;&#12288;&#26085;&#26412;&#35486;&#12364;&#12288;&#12497;&#12540;&#12477;&#12467;&#12531;&#12391;&#12288;&#12363;&#12367;&#12371;&#12392;&#12364;&#12288;&#12391;&#12365;&#12414;&#12377;&#12424;&#65281;&#12288;&#12358;&#12428;&#12375;&#12356;&#65281;

Perfect! I can write Japanese with my computer! Happy!

I got the fault: 

gemgem told me, to use the command

```
im-switch -z zh_tw -s scim
```

What i did now is to use 
```
im-switch -z en_GB -s [COLOR="Red"]scim-anthy[/COLOR]
```

I found this hint here:
[https://wiki.ubuntu.com/InputMethods/SCIM/Setup]("https://wiki.ubuntu.com/InputMethods/SCIM/Setup")

There is an example for chinese input
```
#

With im-switch installed, type im-switch command in the usage of "im-switch [-z <YOUR_LANG>] -s <INPUT_METHOD>" at the terminal prompt (do not with root) so it looks like, for example, :

   im-switch -z en_US -s scim-hangul 

which creates ~/.xinput.d/en_US link to /etc/X11/xinit/xinput.d/scim .

```
So they used scim-hangul.

Just works now!
But maybe I should get an Xubuntu installed on a usb-drive to test which command are really necessary to get it working from out-of-box (in case I stumble above this problem again).

Cant remember which commands I set until this point...

But thx for your help!

---

### Post by Rondonjin on 2006-06-07
> **mogliii]&#12424 said:**
> scim-anthy[/COLOR]
```

I found this hint here:
[https://wiki.ubuntu.com/InputMethods/SCIM/Setup]("https://wiki.ubuntu.com/InputMethods/SCIM/Setup")

There is an example for chinese input
```
#

With im-switch installed, type im-switch command in the usage of "im-switch [-z <YOUR_LANG>] -s <INPUT_METHOD>" at the terminal prompt (do not with root) so it looks like, for example, :

   im-switch -z en_US -s scim-hangul 

which creates ~/.xinput.d/en_US link to /etc/X11/xinit/xinput.d/scim .

```
So they used scim-hangul.

Just works now!
But maybe I should get an Xubuntu installed on a usb-drive to test which command are really necessary to get it working from out-of-box (in case I stumble above this problem again).

Cant remember which commands I set until this point...

But thx for your help!

Eh? Gemgem told you that he/she used im-switch -z zh_tw -s scim but you should use ja_JP.

> i found online that you're supposed to do have "im-switch" INSTALLED first to be able to use this command. so look for it in synaptic. if you can't find "im-switch" in synaptic, go to the repositories list and check everything in the little boxes.

and then type

im-switch -z zh_tw -s scim

but change zh_tw to whatever the code is for japanese. maybe jp_japan or something that looks like that. zh_tw is "chinese traditional for taiwan".

Read the post again.

Wayne

---

### Post by mogliii on 2006-06-07
[QUOTE=Rondonjin]Eh? Gemgem told you that he/she used im-switch -z zh_tw -s scim but you should use ja_JP.



Read the post again.

Wayne[/QUOTE]

Hi,

I marked the change in the command with red color. I used scim-anthy at the end, not scim.

But one more question. When I start my session, and I open a program, it starts typing in japanese. How can I set the initial input to english?

...loving my Xubuntu now :)

---

### Post by ugroh on 2006-06-10
Hi, maybe aou have already solved the problem but since I had the same on my IBM&#12288;X41&#12288;let me tell you how I solved it.

Step 1: Look for the both installation instructions
- Input Methods/SCIM/SCJ/... (on wiki.ubuntu.com/InputMethods/SCIM/...)
- Input Methods/SCIM/Setup (wiki.ubuntu.InputMethods/SCIM/Setup)

Step 2:
follow the instructions in the first wiki. This will not help for firefox but will help for gedit, mail etc.

Step 3:
look at the second wiki for ~/.gnomerc  and add this to the (not existdend) .gnomrc file.

Step 3: logout/login. After thsi, you will see on the taskbar a new sysbol loke a "bügeleisen". If you now start firefox and click on this sysbol, you can chosse anthy for entering japanese in google e.g. . Or shift-space works too.

Impotrant:&#12288;Install all the required laguage support files. I have also installed chinese just for the sake of completness.

I hope it helps. 

Ulrich 

:)

---

### Post by fonggiding on 2006-06-14
That's great that you got your Japanese input working!
I don't understand why so many people choose this difficult route rather than just downloading the Japanese version of Ubuntu. ;) Well I guess if it works for you. Another thing you may want to consider is creating a custom keymap for your keyboard for if you use a non-Japanese keyboard. Just a thought. Does anyone know of a Japanese forum or Ubuntu? 

> Or shift-space works too.
If you don't like that method, I personally am a &#21322;&#35282;/&#20840;&#35282; man myself, then sometimes it is not set as such under your keymap so you may need to change it. For the &#21322;&#35282;/&#20840;&#35282; function to work(in my case I use Dvorak so it didn't) I mapped:
Zenkaku_Hankaku Kanji 
onto key 49. Hope this is helpful!

Oh and just a grammar suggestion:
&#12424;&#12363;&#12387;&#12383;&#65281;&#12497;&#12477;&#12467;&#12531;&#12391;&#26085;&#26412;&#35486;&#12364;&#26360;&#12369;&#12427;&#12424;&#12358;&#12395;&#12394;&#12387;&#12383;&#65281;&#12358;&#12428;&#12375;&#12356;&#65281;

---

