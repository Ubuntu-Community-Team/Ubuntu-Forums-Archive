---
title: "After installing Beryl..."
date: 2007-05-12
forum: Desktop Effects &amp; Customization
---

### Post by churchi on 2007-05-12
hi all,

well I just have a few quick questions today.

I have successfully gotten Beryl installed and working on my system which is great, however a few things have changed after I started to use it.

now these are small things but annoying and I wanted to ask the community how I would get around this.

I am running the latest ubuntu version of feisty. 7.04

the first thing, is now I am using Beryl (latest stable) I have setup my screen to turn off through the admin menu after 15mins. its through a little GUI tool to set the time your pc will sleep and monitor will turn off. currently I have it set at 15mins, however it is not turning off the screen anymore, it just displays my screensaver. it did work before I had installed beryl. dose anyone know how to fix this up? possibly without having to script it at logon, since it was working before.

the 2nd thing is that while beryl is running, and when I click to launch a new program, the program will load however it just stays in the background window and flashes, it will not automatically come to the front of the display. this is quite annoying, since when I click to open a program from the menu, it is pretty obvious that I want to see it straight away and not just in the task bar. I have searched around for ages to try and find this option in beryl, so im just wondering if someone could give me some help in finding out how to make a new program launch, to come to the front and be the active window.

well if anyone can be of some help that would be great, or if you need anymore information then just let me know.

thank you

---

### Post by Martje_001 on 2007-05-13
The second has something to do with windows prevention stealing (or something)...

---

### Post by darkmaster on 2007-05-13
Just open the Beryl-preferences window and set in the main page: Level of focus stealing prevention to Low. 

That's the answer to the second problem only.

---

### Post by churchi on 2007-05-13
> **darkmaster said:**
> Just open the Beryl-preferences window and set in the main page: Level of focus stealing prevention to Low. 

That's the answer to the second problem only.



hey guys, thanks to the above 2 posters, that has now fixed up my windows so they now come to the front.

the option is found on the general tab settings, and if you change it to "normal" or "low" then the window will now show up in the forground when opened.

thanks for the help,

any chance of help with the other problem please? i have found a way to set it by the command line and run a script each time ubuntu boots that will manually set the timeout for a specified amount of time. (using the xset command).
but i was just wondering why the power management tool under system --> Preferances is now not working once beryl is running.

or any other suggestions to get it working under gnome would be great.

thanks,

---

