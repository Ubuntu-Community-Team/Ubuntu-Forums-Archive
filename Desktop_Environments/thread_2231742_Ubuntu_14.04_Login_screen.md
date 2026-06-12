---
title: "Ubuntu 14.04 Login screen"
date: 2014-06-27
forum: Desktop Environments
---

### Post by kakashi_12 on 2014-06-27
How do I disable the list of usernames at log-in? I want to be presented with a UserName field and Password field to manually type full credentials.

I use to do this with Ubuntu Tweak, but the new version does not have that option.

---

### Post by deadflowr on 2014-06-27
Here
[https://wiki.ubuntu.com/LightDM#Hiding_the_User_List](https://wiki.ubuntu.com/LightDM#Hiding_the_User_List)

---

### Post by kakashi_12 on 2014-06-27
Beautiful. Not sure if I had to actually download and install LightDM or not. It looks like it might have already have been there.
```
sudo gedit /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
```

Add this line of text to the bottom of the file:
[SeatDefaults]
greeter-hide-users=true

Now that I did this, it makes the default desktop environment Unity instead of my preferred GNome Medacity.
How do I change that to the default instead of Unity?

I know I can click on the white icon to change it, but I don't want to have to do that every time I log in. I want the default set.

---

### Post by kakashi_12 on 2014-06-27
The other problem is that every time I go to edit a document as root I get an error in the terminal.
[sudo] password for admin2: 
(gedit:2612): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

---

### Post by kakashi_12 on 2014-06-27
I also just received a message at log in that there was a system problem and it gave me an option to Report it.
Not sure what happened or how to read the report.

---

### Post by deadflowr on 2014-06-27
[sudo vs gksu]("http://ubuntuforums.org/showthread.php?t=851911")

---

### Post by deadflowr on 2014-06-27
> **kakashi_12 said:**
> I also just received a message at log in that there was a system problem and it gave me an option to Report it.
Not sure what happened or how to read the report.

If you just hit send and then nothing else happened, then that should be all you needed to do.
If you want to see the crash report, look in /var/crash.

---

### Post by kakashi_12 on 2014-06-27
Error shows problem with the file I edited. What did I do wrong? Should I have done a different file?
ExecutablePath
/usr/bin/unity-greeter

And still don't know how to change the default desktop environment.

Trying to attach the crash reports here, but apparently the txt files are too large.

Is there a more safe or alternative way of doing this besides lightdm? It seems this caused the crash.
Or tell me what I did wrong.

---

### Post by deadflowr on 2014-06-27
> **kakashi_12 said:**
> 
Trying to attach the crash reports here, but apparently the txt files are too large.
[Pastebinit]("https://help.ubuntu.com/community/Pastebinit")
> 
Is there a more safe or alternative way of doing this besides lightdm? It seems this caused the crash.
Or tell me what I did wrong.
You edited the wrong file
from the wiki:
> System provided configuration is stored in **/usr/share/lightdm/lightdm.conf.d/*.conf** and is not user editable. System administrators can override this configuration in **/etc/lightdm/lightdm.conf.d/*.conf** and **/etc/lightdm/lightdm.conf**. Files are read in the above order and combined together to make the LightDM configuration. 

I would suggest re-reading the wiki through.

---

### Post by kakashi_12 on 2014-06-28
Ok, I re-read the wiki. lightdm.conf does not exist with in etc/lightdm directory. Only users.conf exists.

---

### Post by deadflowr on 2014-06-28
> **kakashi_12 said:**
> Ok, I re-read the wiki. lightdm.conf does not exist with in etc/lightdm directory. Only users.conf exists.

So, for fun, I decided to play with this.
First, you need to make the folder /etc/lightdm/lightdm.conf.d
```
sudo mkdir /etc/lightdm/lightdm.conf.d
```
then make the file
(I used nano, but you can use gedit if it's easier.)
for nano, simply run
```
sudo nano
```
for gedit
```
gksu gedit
```
(you might need to install gksu --simply run sudo apt-get install gksu.
as well, gksu sometimes defaults to su and not sudo, if it doesn't accept you sudo/user password open the gksu propeties
```
gksu-properties
```
and change it to sudo if set to su.)

When you set the file and want to save it, make sure to save it in the newly made directory as 50-whatever-name-you-want.conf.
I don't know if you need to reboot or simply logout to test it, I rebooted.
Hope this helps.

---

### Post by kakashi_12 on 2014-06-28
_Final resolution_:
Check to see if this directory exists and contains files (/etc/lightdm/lightdm.conf.d).
If not, create it
```
sudo mkdir /etc/lightdm/lightdm.conf.d
```
Create the file
sudo gedit
Type this text into the file.

[B][SeatDefaults]
allow-guest=false
[/B]
[B][SeatDefaults]
greeter-hide-users=true
[/B]
[B][SeatDefaults]
user-session=gnome-fallback[/B]

Save file to this directory, etc/lightdm/lightdm.conf.d
Name the file, 50-myconf.conf

Reboot.

At login screen, before even typing in credentials click the white icon. You will see that Metacity is the default with the word "(Default)" next to it. "Default" word was cut off on my screen. But I knew it worked!

Worked. Thanks for your help. It was a pain, but it worked. Thanks again!

---

### Post by deadflowr on 2014-06-28
Good to see you figured it out.
As a sidenote: you don't need to have a seatdefaults entry for each one.
simply one should suffice
[SeatDefaults]
First Entry
Second Entry
and so on and so on

But if how you set it up works it works.

---

### Post by kakashi_12 on 2014-07-03
crap, I was getting some error saying 'couldn't load session' or something to that exist. So I started over from scratch and I tried this again and it's not working now. Only one problem.

When I log in with my other user account it does not automatically go to the default desktop environment (gnome fallback). it goes to unity. It does not do that for my admin account. What am I missing here?

Not sure if it matters, but I created the user account after changing these settings.

---

### Post by kakashi_12 on 2014-07-04
The only thing I can get it to do (regardless of what I write in the configuration file) is to MANUALLY choose the session I want for each individual user, log in, then back out. Then the default session will be set for that user. The rest of it works. Weird.

---

### Post by kakashi_12 on 2014-07-05
After awhile, I am once again getting the "System program problem detected" window at log in.
Problem with Executable path /usr/sbin/unity-greeter.
I'm really irritated. I edited the right files. Don't understand why this is still happening.

---

