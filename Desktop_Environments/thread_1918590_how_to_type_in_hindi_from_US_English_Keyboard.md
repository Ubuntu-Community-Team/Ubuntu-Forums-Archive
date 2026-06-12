---
title: "how to type in hindi from US English Keyboard"
date: 2012-02-01
forum: Desktop Environments
---

### Post by jamesbon on 2012-02-01
I opened libreoffice 3.0 (Ubuntu 11.10) and selected Lohit Hindi font in the fonts selection column. Downloaded the charachter map of English and Hindi keys as given here [http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/5/html-single/International_Language_Support_Guide/images/hindi.png](http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/5/html-single/International_Language_Support_Guide/images/hindi.png)

but when I am typing in Hindi with my english keyboard there is no Hindi word I still the english letters typed as "kerasadsd".Which should not happen since Lohit Hindi font is selected so I expected the correcponding key mapped Hindi characters to appear.

Q1)  What mistake did I do in above? I have US English keyboard only and I am using the same to type in Hindi.

Q2) Will the documents made as above will be in unicode if not then what font should I use so that I am able to type in unicode using hindi fonts on libreoffice.

---

### Post by kazztan0325 on 2012-02-01
Hi jamesbon,

Do you have the issue even though you have installed 'Hindi' with **Language Support**?

If then, have you set up Input Method with **ibus settings**?

---

### Post by jamesbon on 2012-02-02
Well I do not know what Language support means.

I am unable to see English as my default language.My system is showing
some Korean or Chinese language which I do not understand.
The system settings folder etc is also opening in chinese I am unable
to use the system now.
Have uploaded the snapshots here please have a look upon a reboot
asked to rename all folders
[https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704405897276606450](https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704405897276606450)
gmail opening in chinese
[https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704406102859334402](https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704406102859334402)
this is how menu on my system looks half english and half chinese
[https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704407869479955202](https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704407869479955202)
if you notice in third snapshot the calendar and menu is appearing in chinese.

I want the original US english menus folder names back.I just wanted
to type a document with Lohit Hindi font in Libreoffice.
Ubuntu 11.10 (I do not use Unity only Gnome desktop. I had installed
gnome-session-fallback long time back and had been using the same).

**The problem has increased now.**

How do I get back to all english submenus and english folder names.I have a US English Keyboard and I use only US English.Some how this thing which is now set is unwanted.

---

### Post by varunendra on 2012-02-02
> **jamesbon said:**
> 
Q1)  What mistake did I do in above? I have US English keyboard only and I am using the same to type in Hindi.

Q2) Will the documents made as above will be in unicode if not then what font should I use so that I am able to type in unicode using hindi fonts on libreoffice.
A1) You need "Hindi Keyboard layout" to be able to type in Hindi, not English.

A2) No matter whatever font you use, it won't type in Unicode unless it is a Unicode keyboard layout. (which again relates back to Ans.1).

> **jamesbon said:**
> Well I do not know what Language support means. it means the 'enabling the system to understand and type' the language/characters you want.

Now onto the solutions:
> **jamesbon said:**
> I want the original US english menus folder names back. In the last screen, where you have opened the "Language Support" dialogue box, just highlight "English" (as you already had while taking the screenshot) > then click the button that says (still in English, fortunately..) "Apply System-wide" > then restart (or log-off > re-log-on). Everything should return to normal.

> **jamesbon said:**
> I just wanted
to type a document with Lohit Hindi font in Libreoffice.
For this, reopen the same "Language Support" dialogue-box, then

[LIST=1]
[*]click on "Install/Remove languages"
[*]put a 'Tick mark' against Hindi
[*]click "Apply changes"
[*]supply your password to authenticate the change
[*]enable "ibus" on the previous dialogue box (you already have)
[*]close the box.
[/LIST]

By doing above, you have installed only support for Hindi typing. Now you also have to add a keyboard layout for Hindi typing. Do this as follows:

[LIST=1]
[*]In "System-Settings, click "Keyboard Layout"
[*]Click on the '**+**' sign at the lower left corner to bring up the layout selection list.
[*]Now, if you are habitual to "Mangal" typing in windows, select "Indian" > click "Add"
[*]Two other options are "Hindi (Bolnagri)" and "Hindi (Wx)". Both are phonetic as far as I can tell. There used to be other layouts as well (one of them very close to Kruti or Chanakya), but I couldn't find them in 11.10 (probably because I haven't installed full lang. support pack yet).
[*]Once added to the 'Keyboard Layout' list, you should see a 'keyboard' icon in the system tray (I'm in Unity, but should be same in Gnome), clicking on which you can choose between different enabled layouts.
[*]Additionally, in the 'Keyboard Layout' box, you can click "Options" > "Key(s) to change layout" to assign a shortcut key-combination to toggle between different layouts (just like Alt+Shift in windows).
[/LIST]
&#2310;&#2358;&#2366; &#2361;&#2376; &#2351;&#2361; &#2310;&#2346;&#2325;&#2368; &#2360;&#2350;&#2360;&#2381;&#2351;&#2366;-&#2360;&#2350;&#2366;&#2343;&#2366;&#2344; &#2350;&#2375; &#2360;&#2361;&#2366;&#2351;&#2325; &#2361;&#2379;&#2327;&#2366; &#2404; :popcorn:

---

### Post by jamesbon on 2012-02-02
Ok great message.With help of a thread here
[http://ubuntuforums.org/showpost.php?p=11658354&postcount=4](http://ubuntuforums.org/showpost.php?p=11658354&postcount=4)
and your message I proceeded upto following point
> **varunendra said:**
> A1) 
By doing above, you have installed only support for Hindi typing. Now you also have to add a keyboard layout for Hindi typing. Do this as follows:

[*]Once added to the 'Keyboard Layout' list, you should see a 'keyboard' icon in the system tray (I'm in Unity, but should be same in Gnome), clicking on which you can choose between different enabled layouts.
[*]Additionally, in the 'Keyboard Layout' box, you can click "Options" > "Key(s) to change layout" to assign a shortcut key-combination to toggle between different layouts (just like Alt+Shift in windows).



I have uploaded a snapshot 
[https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704512525307326930](https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704512525307326930)


in the snapshot top right hand corner you can see a keyboard icon.Which says combination of Keys Ctrl+Space will toggle keyboard. I here after opened libreoffice selected Lohit Hindi and pressed Ctrl+Space but the letters which I typed were still in English.



> **kazztan0325 said:**
> Hi jamesbon,

Do you have the issue even though you have installed 'Hindi' with **Language Support**?

If then, have you set up Input Method with **ibus settings**?
Input method with Ibus settings is greyed out there is no option to enable Hindi as input method
Here is a snapshot
[https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704517018379437426](https://picasaweb.google.com/107404068162388981296/UnknownAsianLanguage#5704517018379437426)

However I feel my problem is related to this one also
[http://ubuntuforums.org/showthread.php?p=11658578#post11658578](http://ubuntuforums.org/showthread.php?p=11658578#post11658578)

---

### Post by varunendra on 2012-02-02
I just tried ibus preferences (both in unity and gnome-fallback), and found the same problem you are facing. I've used it before and there's definitely something wrong with it this time. Can't say at the moment whether it's a bug or a bad consequence of all that "oversimplification" attempts Ubuntu is trying these days.

However, the method I described in my earlier post works both in gnome-fallback and unity. Try that:
> **varunendra said:**
> 

[LIST=1]
[*]In "System-Settings, click "Keyboard Layout"
[*]Click on the '**+**' sign at the lower left corner to bring up the layout selection list.
[*]Now, if you are habitual to "Mangal" typing in windows, select "Indian" > click "Add"......
[/LIST]
I'll try to figure out what's wrong with ibus preferences. For now, please try above and post back how it goes for you.

---

### Post by jamesbon on 2012-02-02
Ok I have been able to fix this. I installed one more package 
```
   ibus-m17n     
```
this is also required.
&#2310;&#2346;&#2325;&#2368; &#2348;&#2366;&#2340; &#2360;&#2350;&#2333; &#2327;&#2399;&#2366; 
but then this method of typing is very difficult mangal type.The keymap is of following kind
[http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/5/html-single/International_Language_Support_Guide/images/hindi.png](http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/5/html-single/International_Language_Support_Guide/images/hindi.png)


I prefer gmail kind of phonetic typing in Hindi.Such as [http://mirror.umd.edu/mozdev/indicime/wx_keyboard.html](http://mirror.umd.edu/mozdev/indicime/wx_keyboard.html)
How to do so and need key map for the same.

---

### Post by varunendra on 2012-02-02
> **jamesbon said:**
> Ok I have been able to fix this. I installed one more package 
```
   ibus-m17n     
```this is also required.
Great! :P
..
..
> **jamesbon said:**
> I prefer gmail kind of phonetic typing in Hindi.Such as [http://mirror.umd.edu/mozdev/indicime/wx_keyboard.html](http://mirror.umd.edu/mozdev/indicime/wx_keyboard.html)
How to do so and need key map for the same.
If you can now get the input selection menu like [this]("http://www.muktware.com/sites/default/files/images/applications/ibus-install-3.jpg") in ibus preferences, then simply 'Add' the "Phonetic" layout.
Or,
In the method I've been talking about, the same thing is done by selecting "Hindi (Wx)".


**_Edit_:**
The other method also gives a keyboard icon same as ibus gives (thus two icons when using both), whose drop-down menu includes the option to "Show current layout".

**_Edit2_:**
Actually, "Phonetic" in ibus and "Wx" in "Keyboard Preferences" don't seem to be same. Although they both (along with some others) are phonetic type. So you may have to figure out the most suitable one for yourself, then you can use the default "Keyboard Preference" method to see its keyboard layout from its drop-down menu.

---

### Post by jamesbon on 2012-02-02
> **varunendra said:**
> simply 'Add' the "Phonetic" layout.
Or,
In the method I've been talking about, the same thing is done by selecting "Hindi (Wx)".

 Hmmm, I can confirm that selecting phonetic as input method is not working as expected.Though I am able to type in Hindi with an INSCRIPT keyboard as shared here [http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/5/html-single/International_Language_Support_Guide/images/hindi.png](http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/5/html-single/International_Language_Support_Guide/images/hindi.png)

---

