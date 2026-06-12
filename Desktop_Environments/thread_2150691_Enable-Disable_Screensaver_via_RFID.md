---
title: "Enable-Disable Screensaver via RFID"
date: 2013-06-01
forum: Desktop Environments
---

### Post by tyeo098 on 2013-06-01
So, I have this el-cheapo RFID scanner and some RFID tags.

I thought to myself, You know what would be neat? Enabling and disabling the lock screen with this thing.

So the package arrived (along with my IBM carbine, woohoo!) and I tore it apart and hooked it up.

This device emulates a USB keyboard (that explains the driver-less thing they were pushing) and essentially, types out the card ID and hits enter.
I thought I could just open a constant stream from /dev/stdin (a la keylogger) and watch for when the card I want was punched in. Thats what lead me to creating this stupid simple script:

```
#!/bin/bash

cat /dev/stdin | while read line
do
    # do stuff
if [ "$line" == "0000996716" ]
then echo "Correct!"
fi

done

```

Which worked!

But, I then changed the THEN statement to say gnome-screensaver unlock command
```
gnome-screensaver-command -d
```

And locked my screen manually. (CTRL+ALT+L) Swiped my card aaand.... nothing. The scanner had just typed the card # in the password field and hit enter, resulting in a 'password incorrect' to show up on the lock screen.
So I unlocked my screen via the password and noticed there was nothing on the terminal screen.
So I opened a direct pipe to /dev/stdin and locked my screen. Unlocked it with my password and... nothing again. Does /dev/stdin not contain information that is being typed during the lock screen? What does?

Haaaaalp D:

---

### Post by tyeo098 on 2013-06-02
Thinking out loud here, but since this emulated a USB keyboard, would it be possible to have 2 passwords attached to my user account?

The script (posted above, slightly modified) can lock the scree, while the secondary password is set to the card id, allowing it to unlock the screen?

I just have have my primary password be set to a bunch of numbers haha

---

### Post by tyeo098 on 2013-06-02
Well I can read SOME kind of input from /dev/input/event3 (the reader) but I cannot decode it.

Can a mod move this to a more appropriate subsection?

---

### Post by tyeo098 on 2013-06-03
Well you guys suck :P
It was kinda specific and niche but I wont hold it against you ;)

Anywho, for the full run down.

I had bought this neat little unit which describes itself as 'driverless' like in the original post. This means it acts like a USB keyboard (and registeres itself as such in /dev/input/event*).
This made it almost useless to me as I couldn’t interact with the device any way when the lock screen was active, I needed to read the keystrokes from the device as they were being 'input' by the reader
Cat-ing /dev/input/event3 (my reader) gave me garbage, or so I though. 

Then I ran into this piece of code here: [http://itech-planet.net/content/reading-device-input-directly-fromto-devinputeventx-ubuntu-c](http://itech-planet.net/content/reading-device-input-directly-fromto-devinputeventx-ubuntu-c) with no? author that I can see, but most of the credit for the legwork in this application goes to him/her. Thanks!
Simplifying this code I was able to read the raw input from my own keyboard, with the secret phrase being 'secret' and proceeded to capture the keystrokes into a variable and look for when 'enter' was hit to check the string against the stored value for the code.

This code is essentially a glorified keylogger pointing to a different 'keyboard' and scanning what it 'types' to a matching phrase. 
Much like how the FBI sifts though millions of AOL IM's from a 13-yo girl looking for terrorists!

When it hits the matching phrase, it triggers the if statement and runs the rest of the corresponding code. I've commented it the best I can, if you have any issues, email/pm/im/yell loudly at me.

Not like you read any of that, you just want the code! Well, here it is!

Usage: ```
 sudo ./[file] -u [your username] -d [location to device] -t [tag id]
```
So I, being Tyler, with my device at /dev/input/event3 and my tag being 0000996716 woudl have:
```
sudo ./input -u tyler -d /dev/input/event3 -t 0000996716
```

CODE:
```
#include <linux/input.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <stdio.h>
#include <unistd.h>
#include <string.h>
int getStatus(){
  FILE *fp;
  char path[128];
  fp = popen("sudo -u tyler gnome-screensaver-command -q", "r");

  fgets(path, sizeof(path)-1, fp);
  pclose(fp);
  printf("%s\n",path);
  if(strcmp("The screensaver is inactive\n",path)==0) 
	return 1;//if screensaver is disabled
  else if(strcmp("The screensaver is active\n",path)==0) 
	return 0;//if screensaver is enabled
  else
	return -1;//wat
}

int main(int argc, char **argv)
{
//char array that stores the keys in order up to like 40 something, DO NOT MESS WITH THE ORDER OF THIS ARRAY. ITS IMPORTANT.
    char arr[]={' ',' ','1','2','3','4','5','6','7','8','9','0','-','=','\b','\t','q','w','e','r','t','y','u','i','o','p','[',']','\n',' ','a','s','d','f','g','h','j','k','l',';',',','`',' ','\\','z','x','c','v','b','n','m',',','.','/',' ','*',' ',' '};
    char inp[256];//input string to check what you type.
    int fd;//file pointer to the /dev/input device
char usr[32];//stores your username to run screensaver command as you. Root user (sudo) can NOT lock the screen.
char tag[32];//stores the tag ID for the RFID
char dev[32];//stores the device location, /dev/input/eventX
char lcom[96];//locking command builder string
char ucom[96];//unlocking command builder string
//processes arguments, dont ask.
   int idx = 0;
   for (idx = 1; idx < argc;  idx++) {
       if (strcmp(argv[idx], "-u") == 0) {
	  strcpy(usr,argv[idx+1]);
          printf("User = %s\n", usr);
       } else if (strcmp(argv[idx], "-t") == 0) {
	  strcpy(tag,argv[idx+1]);
          printf("Tag = %s\n", tag);
       } else if (strcmp(argv[idx], "-d") == 0) {
	  strcpy(dev,argv[idx+1]);
          printf("Device = %s\n", dev);
	  fd = open(dev, O_RDONLY);
       } else {}
    }
    //build commands
    strcpy(lcom,"sudo -u ");
    strcat(lcom,usr);
    strcat(lcom," gnome-screensaver-command -l");
    strcpy(ucom,"sudo -u ");
    strcat(ucom,usr);
    strcat(ucom," gnome-screensaver-command -d");
    struct input_event ev;
    int cursor=0;
    while (1)
    {
        read(fd, &ev, sizeof(struct input_event));
        if(ev.type == 1)//only key ID event
            if(ev.value == 0)//only not repeat
		if(ev.code== 28||ev.code==14){//if code is enter or bsp, reset the counter and compare
			inp[cursor]='\0';//terminate string
			cursor=0;
			if(strcmp(inp,tag)==0){//if input string equals tag, strcmp works funny lol
				int status=getStatus();//find out what the screensaver is doing
				if(status==1){//screensaver is unlocked, so lock it
					printf("Locking...");
					system(lcom);}
				else if(status==0){//screensaver is locked, so unlock it!
					printf("Unlocking...");
					system(ucom);}
				else printf("Wat happened");//???
			}
		}
    		else{//if not enter or bsp, log it		
			inp[cursor]=arr[ev.code];
			cursor++;
		}
	//fflush(stdout);this was here for debug purposes, since apparently I dont know how STDOUT works lol
    }
}
```

---

