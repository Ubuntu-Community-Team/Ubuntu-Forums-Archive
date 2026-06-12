---
title: "Keyboard Layout Options in Ubuntu/Xbuntu"
date: 2011-07-11
forum: Desktop Environments
---

### Post by Zhixin on 2011-07-11
[FONT=Verdana][SIZE=2]I'm a very new user to Linux (Xbuntu), and have figured out how to do most of what I could do in Windows. There is one problem, though.

For my work, I need to be able to type a lot of words with diacritical marks, like[/SIZE][/FONT][FONT=Verdana][SIZE=2] &#333;, ü, &#335;, and so on. My main working language is English and these other words are from a lot of other languages, so it wouldn't be practical to change my entire keyboard layout to something besides QWERTY. These words come up often enough that it would be very helpful to be able to assign shortcut keys to them.[/SIZE][/FONT]

[FONT=Verdana][SIZE=2]I found a helpful blog post that explains exactly how to do what I want. I don't know if posting web addresses on this forum is allowed, so for now I'll just explain. The blogger has set up his Ubuntu system so that, for example, he types [Alt Gr] ["] [u] and gets the letter ü. He does it from this menu:[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]> "Settings" > "Preferences" > "Keyboard" > "Layouts" > "Layout Options"[/SIZE][/FONT]


[FONT=Verdana][SIZE=2]The problem is that Xbuntu doesn't have a "Layout Options" button on the "Layouts" preference page. The page only allows pre-existing keyboard layouts to be selected, with no way to customize.[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]
[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]So here is my question: Is there a way to do this by bypassing the Preferences GUI, either through the Xubuntu Preferences Editor or from the command line? 
[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]
[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]As long as it works in LibreOffice Writer I'll be happy. What I'm really trying to do is recreate the functionality of the Insert > Symbol > Shortcut Key function in MSWord, but it looks like this may be easier to do through the global Preferences than through LibreOffice itself. 
[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]
[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]My apologies for the long question. I'll be very grateful for any ideas.
[/SIZE][/FONT]

---

### Post by Zhixin on 2011-07-14
After silence from the community (are Linux users all monolingual?) and more searching on my part, it looks like the answer is to learn about Compose Key sequences. Here's the standard documentation, in case anyone else has a similar question to mine:

[https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey)

I haven't had time to try it, though.

---

### Post by Zhixin on 2011-07-18
I've made more progress in finding out what the problem is, though so sign of a solution yet.



In Ubuntu there are two easy solutions under ¨System  Preferences-->Keyboard Layout¨. Both of them use ¨dead keys¨ to type  letters with diacritical marks and other special characters.

 1. ¨USA - Alternative International¨, which makes it possible to type my &#362; and Ö very easily using the Alt Gr (right Alt) key.
 2. Designate a ¨Compose Key¨, which can be used in certain key combinations to type various kinds of characters.
 Here´s the problem:
 Both of these methods work fine in Libreoffice Writer, as long as IBUS isn´t installed.
 With IBUS installed, they work fine in ALL OTHER APPLICATIONS.  Terminal console, text editor, Firefox, file manager, and even Abiword,  in both Kubuntu and Xubuntu.

 But neither of these methods works in Writer once I install IBUS. For  example, <AltGr+-><o> gives me ¨-o¨ instead of the &#333; I  would get otherwise. The Compose Key stops working (in LO) also. The  problem in Libreoffice goes away when I uninstall IBUS, and reappears  (only in LibreOffice) when I reinstall and reselect it. The dead keys  get disabled as soon as IBUS is selected in the system preferences, even  when I haven´t installed the input method for any particular language.
 So that´s everything I know about the problem. To summarize:

 IBUS + other applications => fine
 no IBUS + Writer => fine

 yes IBUS + Writer => no dead key input

 Is this happening to anyone else? 

 Any suggestions about how to fix it?

---

### Post by Ashraf_2003 on 2011-09-04
same problem, please help.............

---

### Post by majedaly on 2011-11-19
I had some similar problem with Arabic characters, installing the language pack solved it for me

---

