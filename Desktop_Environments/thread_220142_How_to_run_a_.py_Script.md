---
title: "How to run a .py Script"
date: 2006-07-21
forum: Desktop Environments
---

### Post by Flashstar on 2006-07-21
I was just wondering how you run a .py script in ubuntu. I am trying to use the edna mp3 server and I need to know how to run a python script to start it. Thanks

---

### Post by RAOF on 2006-07-21
Option 1:
```
python *script*.py
```
Option 2:
Mark the script as executable.  Need only be done once
```
cd */path/to/script*
sudo chmod +x *script*.py
```
Then run it:
```
*/path/to/script/script*.py
```

---

### Post by Flashstar on 2006-07-21
Thanks a bunch that worked! I'm such a noob lol. I was trying all sorts of commands like % python... and ! python... etc. Now I finally got a music server to run on my linux box. :)

---

### Post by Skia_42 on 2006-07-21
It's also a good idea to add the > #!/usr/bin/env python header to the script. it tells the terminal what to use when executing the script.

---

### Post by Flashstar on 2006-07-21
I've just configured it to run in a terminal so all is great. It would just be nice if I could add a working link to my desktop though.

---

### Post by wolterh on 2008-02-11
Well links are easy, just right click file and select Make Link. Then drag it to your desktop.

I have one question. What command should I use to add an "open with" open to .py files so that they automatically start a terminal and run?

---

