---
title: "Terminal not working"
date: 2006-10-02
forum: Desktop Environments
---

### Post by HondaDirtBiker on 2006-10-02
When I run the gnome-terminal it shows in the task bar as "Starting Terminal" then closes without loading.
Just before it stopped working I was messing with nautilus, desktop in gConf.
I am using ubuntu with gnome.
What could make the terminal stop working?
Thank you

---

### Post by x64Jimbo on 2006-10-02
if the path to the app got changed, that would bugger it up really good. Open your AlaCarte menu editor and check to see if the path to the command terminal is still mapped correctly.

---

### Post by HondaDirtBiker on 2006-10-02
I checked the command says "gnome-terminal" and the location is "/usr/share/applications". I belive that was working before.

---

### Post by x64Jimbo on 2006-10-02
Go to a term window by pressing ctrl+alt+F4
Login, then do this:
sudo updatedb
this command updates a file index in your hard disk. it will take a bit.
Next, type this:
locate gnome-terminal
find the line that represents your program and its path, then try executing it in gui mode back in X. To switch back, type ctrl+alt+F7.

---

### Post by HondaDirtBiker on 2006-10-03
When I press ctrl + alt + f4 I get a black screen with nothing on it. I waited there for a couple of mins.

---

### Post by x64Jimbo on 2006-10-04
try F5 and F6 separately.

---

### Post by chalex on 2006-10-04
When I run the command "which gnome-terminal", it says /usr/bin/gnome-terminal, so that's where your executable should be.

You could try making a new launcher with that information and see what happens.

---

