---
title: "Need a script to run after a certain user logs in and before the gnome session starts"
date: 2010-05-18
forum: Desktop Environments
---

### Post by McKeegan on 2010-05-18
Hi all,

I have a need for a script to run any time a certain user (or group) is logged in from GDM, but before the GNOME session actually starts.

**Scenario:**
1. Presented with the GDB login screen (regardless of cold boot or other user logout)
2. Log in as user 'student'
3. Whenever 'student' logs in, a shell (or some popup occurs, I don't care about the method) is launched that asks how long the user can stay logged in for. The window session is prevented from loading until an input is received.
4. After the specified time has transpired, the user is automatically logged out.

**Code I more or less want to execute:**
```
echo "How long shall I stay logged in?"
read waitTime
let seconds=$waitTime*60

# Allow me some way to not be auto-logged out
# while I am logged in as a student

if [ $seconds -eq 0 ] ; then
    exit 
else

sleep $seconds && gnome-session-save --kill --silent

fi

exit
```

The code itself isn't the most important thing, I really just want to somehow achieve the functionality I mentioned in the **Scenario**.

I've also realized that running the above script in a terminal requires that terminal to stay open. Even after backgrounding the command, closing the terminal cancels the process. So, I'd need a way to have this script accept input and then run with no non-root user way of cancelling it.

**Things I've tried:**
I've modified the PostLogin and PreSession scripts in /etc/gdm/ with various implementations of the code above.

What happens with this method is I'm usually brought to a black screen and nothing happens. CTRL-ALT-F1 brings me down to a terminal and shows a prompt waiting for input on how long I want the user to be logged in.

I've also modified the gnome.desktop Exec line to point to a script containing the code, but it doesn't seem to do anything. I reckon it just falls back to the TryExec or whatever line.

Can anyone help?

---

### Post by McKeegan on 2010-05-19
Wow, I didn't think this request was going to be so difficult for the Ubuntu community. So, let's change things up a bit, then.

It doesn't necessarily need to be a script and I don't care if the prompt displays for all users, a single user, or a single group. Really, I don't care how it's done. :)

I just need some kind of prompt to load (before the desktop is displayed) that requires an integer input, which it uses to automatically log the user off after the provided time has transpired.

Am I really asking for something that unusual? It doesn't seem that strange to me. Has this never been done before? :confused:

EDIT: Am I asking in the wrong forum? Should I take this elsewhere? Come on, guys, somebody point me somewhere. :)

---

### Post by portentum on 2010-05-19
Unfortunately I'm not familiar enough with bash scripting to write an example script, but it sounds like your script was running as it should at the appropriate time, just unable to display itself - which makes sense, since it's just a shell script and run in the terminal and there isn't one on screen to display it. However, I've run scripts that *do* present a little GUI, so I know what you're asking for is possible.

Unfortunately [this]("http://www.linuxquestions.org/questions/programming-9/makign-a-gui-for-a-bash-script-561451/") is the best I've found so far, I hope it is of some help. (there are plenty of google results for this, most recommending the same programs listed in that thread)

---

### Post by liquidsunshine@gmail.com on 2010-07-05
Try something like:

```
xterm -e "scriptname.sh"
```

Which will pop up an xterm window with the script automatically running in it.  

Another problem I notice with your script is the line:

```
sleep $seconds && gnome-session-save --kill --silent
```

The problem with this being in the PreSession is that it will never actually get to the session (it will just sleep for a while and then kill the session).

Try something like:
```
(sleep $seconds && gnome-session-save --kill --silent) &
```
This will put that entire section in the background and allow the PreSession script to conclude, starting the session.
Though note that the syntax may be wrong since I lost the script that I used that trick in a while ago...

---

