---
title: "Simple script question"
date: 2009-05-08
forum: General Help
---

### Post by lesodk on 2009-05-08
I have made a script called

xtime.sh

where can i put it, such that i can start the program from the terminal 
with

xtime

anywhere.

Is it possible to do it somewhere in the home directory, if i don't have root acces?

---

### Post by MysticalRiotCandy on 2009-05-08
You really can put it anywhere. You just need to set the permission settings to allow you to run the script first.

We'll say you put the script in ~/bin (this would be /home/yourusername/bin).

$ chmod 777 ~/bin/xtime.sh

What this does is it allows anyone and everyone to read, write, and execute this script.  You may not want to allow everyone; in that case, you might use the 700 operator instead of 777 to allow only the owner (you) to read/write/execute (on the man page, it'll read as r, w, and x).

$ ~/bin/xtime.sh

This will run your script.

---

### Post by blazemore on 2009-05-08
Copy the script to your /usr/bin folder:
```
sudo cp xterm.sh /usr/bin/xterm
```

Make the script executable:
```
sudo chmod +x /usr/bin/xterm
```

Profit!
```
xterm
```

---

### Post by kerry_s on 2009-05-08
> Is it possible to do it somewhere in the home directory, if i don't have root acces?

create a folder in your home called /bin, put it in there.

---

### Post by _Purple_ on 2009-05-08
> **lesodk said:**
> I have made a script called

xtime.sh

where can i put it, such that i can start the program from the terminal 
with

xtime

anywhere.

Is it possible to do it somewhere in the home directory, if i don't have root acces?

Name the script xtime. You can create a directory ~/bin using 
```
mkdir ~/bin
```
Then move your file to that folder
```
mv xtime ~/bin/
```
Then make the script executable 
```
chmod u+x ~/bin/xtime
```

Now run the following command
```
echo $PATH
```
This will show the list of directories which will be searched for the executable files. To add your ~/bin directory to this list, open the file ~/.bashrc
```
gedit ~/.bashrc
```

Then add these lines at the end
```
PATH=$PATH:/home/administrator/bin
export PATH
```

Save and reboot. Then if you run this command again, you new path will appear in the list
```
echo $PATH
```
Now you can type xtime from anywhere to run your script.

---

### Post by mcduck on 2009-05-08
Actually ~/bin will be included in user's path automatically if it exists. So just create the directory, put your programs there and it will work.

(you might have to log out and back again after creating the ~/bin before it's recognized)

edit: in case you wonder if this is true and how does it work, take a look at ~/.profile.. :)

---

### Post by lesodk on 2009-05-08
Thanks. Works perfectly!

---

