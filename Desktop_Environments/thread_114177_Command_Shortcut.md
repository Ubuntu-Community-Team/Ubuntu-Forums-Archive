---
title: "Command Shortcut?"
date: 2006-01-08
forum: Desktop Environments
---

### Post by shade11 on 2006-01-08
I have been asking alot of questions today, havent I? Well I am almost through asking all of them. This is my second to last question. . .

I have installed a program that only runs in the terminal.

I want to know if it is possible to create a Launcher on my desktop that when I click on it it activates a command in the terminal. Please tell me if this is possible. And if so please tell me how I can do this.

Thanks a bunch,
-shade11

---

### Post by aysiu on 2006-01-08
Yes.
In the launcher's properties dialogue, check the box that says "Run in terminal."

---

### Post by shade11 on 2006-01-08
Hmmm. I see that it doesn't work. I tried it with some other commands and it works but not this.

I tried using these two commands:

```
pavcl
```
-=and=-
```
pavcl -aut
```

Yes that is Panda Antivirus. I cannot live without an antivirus even if I am using Linux. And plus my school also requires one and we have many Ubuntu users at my school and I dont want to take any risk.

So what, will it just not work with that command?

---

### Post by Ubluntu on 2006-01-08
I had the same problem, I don't really know what the right way to do it is, but I had some luck doing this:

I wanted to run the command:
kill `pidof gam_server`
with a launcher so I didn't have to keep typing it in, For some reason it just won't work in a launcher, especially for startup entries.

I made a file called killgam.sh and entered one line:
kill `pidof gam_server`
and saved it. then i run the command, or make a shortcut, or make a startup entry that looks something like
sh /filelocation/killgam.sh
or
sh ./filelocation/killgam.sh
or
./filelocation/killgam.sh

I think it might be different for some systems.
I hope this helps, send me a private message if you don't understand something

---

### Post by shade11 on 2006-01-08
Nope, no Luck.

---

### Post by Azriphale on 2006-01-08
I just installed the free Linux version of pavcl.

I guess when you tell the launcher to run it in the console, a window pops up, but before you can see what it said, it disappears. At least thats what happened when I ran "pavcl -help"

I came up with a couple of solutions for you. The first is bad. Just, well, bad. Its a C++ app that calls your scan, then pauses when the scan finishes. Don't use this. But here it is anyway:

```

#include <iostream>

using namespace std;

int main() {
  system("pavcl -aut"); // sends this command to the system, running your scan
  cout << "\nPress Enter to continue\n"; // outputs a nice message
  cin.sync(); // clear the input
  cin.get(); // wait for an Enter key
  return 0; // exit
}


```

put that in scan.cpp
install build-essential so you can compile it:
```
g++ -o scan scan.cpp
```

If you put that into a launcher and tell it to run in the console, it should work.

----

The solution that you should use is a bash script. put the following into a file called something like "scan.sh" in your home directory:

```

#!/bin/bash

# The above tells the system to run the script in the Bash shell

pavcl -aut                # run the scan
echo                      # print a blank line
echo Press Enter to exit  # print the exit message
read pause                # wait for input


```
save and close the editor and go into the console. 
Give it execute permissions by typing:
```
chmod u+x scan.sh
```

test the script by typing
```
./scan.sh
```

put "~/scan.sh" into a launcher to run in the terminal. (Assuming you had the script in your home directory, which I recommend).

---

### Post by aysiu on 2006-01-08
[QUOTE=shade11]
Yes that is Panda Antivirus. I cannot live without an antivirus even if I am using Linux. And plus my school also requires one and we have many Ubuntu users at my school and I dont want to take any risk.[/QUOTE] If you have to run it, why not go to System > Preferences > Sessions > Startup Programs and add it there?

---

### Post by shade11 on 2006-01-08
[QUOTE=Azriphale]
The solution that you should use is a bash script. put the following into a file called something like "scan.sh" in your home directory:

```

#!/bin/bash

# The above tells the system to run the script in the Bash shell

pavcl -aut                # run the scan
echo                      # print a blank line
echo Press Enter to exit  # print the exit message
read pause                # wait for input


```
save and close the editor and go into the console. 
Give it execute permissions by typing:
```
chmod u+x scan.sh
```
[/QUOTE]

I cant thank you enough for that idea. I tried it out and it worked. I would have never thought of that

---

### Post by Azriphale on 2006-01-09
I am glad I could help you.

---

