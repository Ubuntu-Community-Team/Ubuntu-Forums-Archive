---
title: "Installing ADOM"
date: 2009-01-28
forum: Gaming &amp; Leisure
---

### Post by Evil Ninja on 2009-01-28
I'm trying to install [ADOM]("http://www.adom.de/") and I'm misunderstanding the instructions in the [Readme.1st]("http://www.adom.de/adom/readme1st.php3"). Could someone help me out?

---

### Post by insanity99 on 2009-01-28
man oh man the months i have wasted playing that awesome game :D though i am new to linux and dont know much about installing unless it is in synaptic sorry.

nethack is in synaptic, dont know if you like it or not

---

### Post by Evil Ninja on 2009-01-28
I have all the roguelike's in Synaptic installed already. :)

---

### Post by Evil Ninja on 2009-01-29
Can anyone help me out? :|

---

### Post by kutagh on 2009-01-29
Are you an administrator/root user?

---

### Post by Evil Ninja on 2009-01-29
> **kutagh said:**
> Are you an administrator/root user?

Yeah, and the only user on the computer.

---

### Post by kutagh on 2009-01-29
Basically the readme tells you to do this after uncompressing:
Go to terminal and enter this command:
```
gksudo gedit /etc/group
```
At the bottom, add "adomown:X::adomown"
Replace X with a number starting from 100 that hasn't been used by a different group in that file. Remember the number as you need to use it once more. Do control+o to save and control+x to exit.
Then enter this command:
```
gksudo gedit /etc/passwd
```
At the bottom, add "adomown:X:::adomown:/usr/games:"
Replace X with the number you used earlier.
Then copy the adom-binary to the folder /usr/games, then go to terminal and cd it to /usr/games and enter the following commands:
```
 chown adomown.adomown adom
chmod +x adom
chmod +s adom
```
Then go to /var/lib and create the folder /adom there. Then in terminal, enter the following commands:
```
chown adomown.adomown /var/lib/adom
chmod 775 /var/lib/adom
```
Then go to /etc and create a new text file called adom_ds.cfg and inside that file it should say:
```
/var/lib/adom
```
Then copy the .adom.cfg file to the home directory.

Let me know if that worked.

---

### Post by Shockwave612 on 2009-01-29
I have this problem too. Thanks kutagh so far, but I have a problem with your instructions. When I try to copy the binary its /usr/games/ it tells me I do not have the permission. The binary itself I have permission for but not for /usr/games/. I tried Properties>Permissions but it told me that I could not change it because I do not own it. Could you please tell me how to remedy this?

---

### Post by kutagh on 2009-01-29
Have you tried copying through the terminal and start with the sudo command, like this:
```
sudo copy /adom-binary /usr/games
```
I'm not sure what command it is for copy, so replace that if needed, but you should get the idea.

---

### Post by insanity99 on 2009-01-29
dont want to go off topic here but is there a way to play nethack on ACSII mode rather than tiles?

---

### Post by Evil Ninja on 2009-01-29
> **insanity99 said:**
> dont want to go off topic here but is there a way to play nethack on ACSII mode rather than tiles?

```
sudo apt-get install nethack-console
```

Play it from the terminal. Best way to play it imo.

--

For some reason I can't move the ADOM binary into usr/games/. :| Says I don't have permission.

---

### Post by Shockwave612 on 2009-01-30
> **kutagh said:**
> Have you tried copying through the terminal and start with the sudo command, like this:
```
sudo cp /adom-binary /usr/games
```
I'm not sure what command it is for copy, so replace that if needed, but you should get the idea.

Thank you, that solved my problem. Now another. :(
When I cd to /usr/games/ then ```
chown adomown.adomown adom

``` I get this message: [QUOTE=TERMINAL]chown: invalid user: `adomown.adomown'[/QUOTE]
I have no experience with these groups or users, any help appreciated.

---

### Post by kutagh on 2009-01-30
Did you properly create the groups and save them (first ctrl+o and then ctrl+x to close) as well as assigning them both the same ID (the X is supposed to be an ID with a number greater then 99 and not being used by a different group)?
It's the easiest if you tell us what you've done so far to try to rectify the problem. Alternatively, copy and paste the /etc/group and /etc/passwd files here so we can take a look at it.

---

### Post by Shockwave612 on 2009-01-30
This is the groups:
> clamav:x:126:
adomown:127::adomown

And the passwd:
> clamav:x:112:126::/var/lib/clamav:/bin/false
adomown:127:::adomown:/usr/games:

There the same number, obviously 1 after 126. Don't know whats happening.

Edit: I pasted directly from your post.
Edit2: Also instead of Ctrl+O (that wanted to open a new file) I clicked save and closed it by clicking the X (top right) instead of Ctrl+X, if that makes a difference.

---

### Post by kutagh on 2009-01-30
Hmmmmm, oughta not to make a difference how you saved it, you either have a different method of editing or whatever but as long as it saves properly, no problem there. It appears to be good. I'm not that much of a pro to see what is the problem right now.

---

### Post by Shockwave612 on 2009-01-31
Thanks anyway, I'll google for help, otherwise I'll just have to wait for somebody who knows what I should do.

---

### Post by Evil Ninja on 2009-02-01
Can anyone help me out with my problem? :| (Top of the page.)

---

### Post by kutagh on 2009-02-01
Have you tried the suggestion of my post, using ```
sudo cp adom-binary /usr/games
``` Because someone also said they had that problem and this solved it for them.

---

### Post by zioAvi on 2009-10-08
Hello, followed the instructions but I'm stuck where you have to copy the .adom.cfg file to the home directory.

Where I get this file? In the package I downloaded there is not such file.

Any help really appreciated thanks

---

### Post by AckSed on 2010-04-27
A local installation does not work,as it refuses to run it,no matter what I do:
```
colin[adom]$ ./adom
bash: ./adom: No such file or directory
colin[adom]$ /home/colin/adom/adom
bash: /home/colin/adom/adom: No such file or directory
colin[adom]$ 
```

Copied the binary from my previous local install. I tried creating the group as instructed,using sudo -i to give myself root:
```
**/etc/group**
adomown:199::adomown

**/etc/passwd**
adomown:199:::adomown:/usr/games
```
Result:
```

root@nori:/usr/games# chown adomown.adomown adom 
chown: invalid user: `adomown.adomown'
```

Looking down the fields in both files,I noticed a theme. So I tried modifying it to match:
```
[B]/etc/group
[/B]adomown:x:199:adomown

**/etc/passwd**
adomown:x:199:adomown:/usr/games/
```
Tried again:
```
root@nori:/usr/games# chown adomown.adomown adom 
chown: invalid user: `adomown.adomown'
```

Bugger.

Nevertheless,I went ahead and created /var/lib/adom/, /etc/adom_ds.cfg and /home/colin/.adom.cfg. Obviously,I couldn't give them ownership of a group that it said didn't exist.

Browsing down the list of groups,I saw there's a "games" group there already,so I added it,just to see if it'd go through:
```
root@nori:/usr/games# chown games adom 
root@nori:/usr/games#
```
It did. Yay.

Now what? Just add everything to the "games" group?

---

### Post by xczxc on 2010-07-17
I'm facing another problem. I was able to launch adom using the cd /home/username/blahblah ./adom command in the terminal (it asked me to rezise the terminal, i did so and worked fine. Then I tried to create a launcher in which I failed and then tried to rezise the terminal automatically. but the thing is that now when I try to play adom using the same way i did it the first and only time I got it to work, this message appears:

ADOM session aborted due to an external problem. 
 * Problem Description: ADOM is either already running or the file '/home/username/.adom.data/.adom.prc'
                        was not removed. 
                        Unable to start. 

  Ihave no idea what is happening

EDIT: Fixed it. The folder was hidden, I founded and deleted it. Now everything is fine.

---

