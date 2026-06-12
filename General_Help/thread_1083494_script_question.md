---
title: "script question"
date: 2009-03-01
forum: General Help
---

### Post by sr_guy on 2009-03-01
I created a script to grab a tv stream with mplayer to send it to a .mpg file on my harddrive. What directory does the script file need to be in to run it automatically with the stript command from anywhere in console? I don't want to change directories to run the script file, I just want to type in ./tv.sh and it'll run automatically.

---

### Post by taurus on 2009-03-01
You can create a ~/bin and place your own personal scripts there.  Then, add ~/bin to your path so you can run them anywhere you want and if they are on your path, you do not need to include the ./ in front of the name.

```
mkdir ~/bin
```
Move your tv.sh to ~/bin and make sure it has an executable permission.  You can now add ~/bin to your path by editing ~/.bashrc.

```
gedit ~/.bashrc
```
Add these two lines to the end of it.

```
PATH=$PATH:~/bin
export PATH
```
Save it and run

```
source ~/.bashrc
```
No ~/bin should be in your path.

---

