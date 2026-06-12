---
title: "gmail notifier that works in Ubuntu 12.04 64bit"
date: 2012-05-15
forum: Desktop Environments
---

### Post by Oldhacker on 2012-05-15
As it stands now, in order to check my Gmail (which I use as my primary email account,) I have to open up Firefox, then click the Google search bar, then click Gmail - all too often find out that I have NO incoming email.

The Ubuntu software center has an app that had very poor user evaluations. After installing it and seeing it fail to function, I understand why.

Is there anything available that will give me a visual indicator on the desktop when there is something new in my Gmail inbox?

---

### Post by 3Miro on 2012-05-15
Under Chrome/Chromium, there is an extension that will give you a gmail indicator in your browser. This was the primary way for me to keep track of my mail, any time I am on-line I will be aware if I have new gmail messages.

Not I use Thunderbird, I let it run minimized in the Unity dash and it lets me know with a message popup whenever I have new mail. I also get the +1 indicator on the Thunderbird icon.

Firefox is messing with me right now, but you can check for a Gmail addon for Firefox, since this is the browser that you seem to be using.

---

### Post by Rodney9 on 2012-05-15
I use GMail Watcher in Firefox, it blinks, plays a sound and counts how many new emails. 

[https://addons.mozilla.org/en-US/firefox/addon/gmail-watcher/](https://addons.mozilla.org/en-US/firefox/addon/gmail-watcher/)

Rodney

---

### Post by markbl on 2012-05-15
IMHO, the best gmail notifier for Ubuntu Unity is gm-notify. It is in the standard packages. AFAIK, it is the only notifier which notifies immediately. All other notifiers work by poll only.

---

### Post by Oldhacker on 2012-05-16
Thanks to all who have responded to my query.
Gm-notify sounded like what I was looking for, inasmuch as the other choices operated from within a browser and wouldn't be of use if I were not in a browser and working on a Document, Spreadsheet, Graphic or such.

I installed with "sudo apt-get install gm-notify"
and did not receive any error messages. However, since installing gm-notify yesterday, I have received a dozen e-mails and no indicator ever showed up on my desktop. It is a "puzzelment" (as was phrased in The King and I.)

---

### Post by 3Miro on 2012-05-16
You probably need to start gm-notify, try running it form the Unity menu. You may have to add it to the startup programs via the computer icon in the top-right -> startup applications.

---

### Post by hakermania on 2012-05-16
Hello Oldhacker, I have a very simply and light solution for you!

That's a working script:
```

#!/bin/bash

check_emails(){
count=0;

#FIRST ACCOUNT
gmail_login="FISRT_ACCOUNT_HERE@gmail.com"
gmail_password="FIRST_PASSWORD_HERE" 
count=$(wget -q -O - https://mail.google.com/a/gmail.com/feed/atom --http-user=${gmail_login} --http-password=${gmail_password} --no-check-certificate | grep fullcount | sed 's/<[^0-9]*>//g')

if [ $count -gt 0 ]; then
   notify-send "GMAIL" "$gmail_login - $count new emails"
fi

#SECOND ACCOUNT
gmail_login="SECOND_ACCOUNT_HERE@gmail.com"
gmail_password="SECOND_PASSWORD_HERE" 
count=$(wget -q -O - https://mail.google.com/a/gmail.com/feed/atom --http-user=${gmail_login} --http-password=${gmail_password} --no-check-certificate | grep fullcount | sed 's/<[^0-9]*>//g')

if [ $count -gt 0 ]; then
   notify-send "GMAIL" "$gmail_login - $count new emails"
fi
}

#PROGRAM STARTS HERE
#timeout in case you have selected starting the script in startup
sleep 5 #set your own timeout if you want
while true; do
   check_emails #run the function
   sleep 15m #timeout to wait between each check
done

```You should change the words in capital and everything after the 'sleep' commands, it is the timeout.

You can repeat the same thing in the function check_emails for any gmail accounts you want to.

EDIT: forgot to add that you have to install the package that contains the command notify-send, I think it is libnotify-bin or similar.
Also, you can place the script in your startup applications!

---

### Post by markbl on 2012-05-16
> **Oldhacker said:**
> 
I installed with "sudo apt-get install gm-notify"
and did not receive any error messages. However, since installing gm-notify yesterday, I have received a dozen e-mails and no indicator ever showed up on my desktop.
Sorry if this is a stupid question but you did configure it didn't you? Run gm-notify-config from dash etc. It needs to know your google account details.

---

### Post by Oldhacker on 2012-05-16
Not a stupid question at all. I have made many stupid errors that should have been obvious, but not configuring this was not one of them. ;-)

As it stands now, I can bring up gm-notify from the command line, but it only remains visiblefor a few seconds. Tomorrow, I plan on trying to figure out how to put it in my start-up applications and see if it can function without command line input.

If that does not work, I'll try the script that another Ubuntuist kindly posted. This Ubuntu group sets a shining example of how people can and should help one another.

---

### Post by markbl on 2012-05-17
> **Oldhacker said:**
> Tomorrow, I plan on trying to figure out how to put it in my start-up applications

You ask the above question but did you not see the checkbox item "Start automatically on logon" in the gm-notify-config app I referred above?

---

### Post by Oldhacker on 2012-05-17
I did miss that "Start automatically on logon" which was located in the "advanced" tab. Now that I checked that one and re-booted, we shall see when and if it works. ;-)

---

### Post by Oldhacker on 2012-05-17
Because I was anxious to see if this app really worked and no new e-mails were coming in, I sent myself a short test message from another account.
The little window did appear nicely in the upper right hand corner of the screen. However, it only lasts for about ten seconds. If one is absorbed in another task, it could easily be missed. Is there any way to modify the app for the message to remain in place until acknowleged?

---

### Post by hakermania on 2012-05-17
> **Oldhacker said:**
> Because I was anxious to see if this app really worked and no new e-mails were coming in, I sent myself a short test message from another account.
The little window did appear nicely in the upper right hand corner of the screen. However, it only lasts for about ten seconds. If one is absorbed in another task, it could easily be missed. Is there any way to modify the app for the message to remain in place until acknowleged?

In order to modify that application, you would maybe had to look at the code of it, and if it isn't any script, then you will have to recompile it - too much work.

On the other hand, if you work with my script, all you have to do is to alter all lines containing
```
notify-send
```
with
```
zenity --info --text "$gmail_login - $count"
```or maybe keep both of them, so as to be sure that you saw them.
Zenity will create a messagebox right on your face, and it will stay there untill you click OK :)

---

### Post by Oldhacker on 2012-05-18
I am certain that your script is correct, but I must be getting rusty with my editing and saving technique. I cut it down to my single Gmail account, made what I think is your most recent alteration, chmod 777 and put it in /usr/local/bin so as to be on the PATH. But, I must have missed something else.

#!/bin/bash

check_emails(){
count=0;

#FIRST ACCOUNT
gmail_login="***********@gmail.com"
gmail_password="***********" 
count=$(wget -q -O - [https://mail.google.com/a/gmail.com/feed/atom](https://mail.google.com/a/gmail.com/feed/atom) --http-user=${gmail_login} --http-password=${gmail_password} --no-check-certificate | grep fullcount | sed 's/<[^0-9]*>//g')

if [ $count -gt 0 ]; then
     zenity --info --text "$gmail_login - $count"
fi

}

#PROGRAM STARTS HERE
#timeout in case you have selected starting the script in startup
sleep 5 #set your own timeout if you want
while true; do
   check_emails #run the function
   sleep 5m #timeout to wait between each check
done

---

### Post by tumutanzi.com on 2012-05-18
I used to use a small app to do the check work, but now I just stick to the web mail of gmail, since I check mail twice per day.

---

### Post by markbl on 2012-05-18
> **tumutanzi.com said:**
> I used to use a small app to do the check work, but now I just stick to the web mail of gmail, since I check mail twice per day.
Note that if you use google chrome browser then you can enable "Desktop Notifications" in your gmail settings and chrome will pop up a little notification window on your Desktop when new mail arrives, so long as you have gmail open in a tab somewhere.

---

### Post by unibroker on 2012-05-18
> **markbl said:**
> Note that if you use google chrome browser then you can enable "Desktop Notifications" in your gmail settings and chrome will pop up a little notification window on your Desktop when new mail arrives, so long as you have gmail open in a tab somewhere.
But that message appears and disappears too quickly if you are absorbed in something else.  You can periodically check the tab that gmail is open in as it has a counter to show new mail.  The one thing I miss is the notification sound.  I have never been able to get it to work since coming over to Ubuntu from WinXP.

---

### Post by markbl on 2012-05-18
> **unibroker said:**
> But that message appears and disappears too quickly if you are absorbed in something else.  You can periodically check the tab that gmail is open in as it has a counter to show new mail.  The one thing I miss is the notification sound.
As I said earlier in this thread, gm-notify is the best gmail notifier for ubuntu and sounds like what you want. It notifies immediately on new email, not by polling like most(/all?) other notifiers. It outputs a configurable audio sound, and it lights a static mail icon indicator which stays lit while you have unread google email (although that indicator only works in Unity, not gnome-shell unfortunately).

---

### Post by unibroker on 2012-05-19
> **markbl said:**
> IMHO, the best gmail notifier for Ubuntu Unity is gm-notify. It is in the standard packages. AFAIK, it is the only notifier which notifies immediately. All other notifiers work by poll only.

Installed it last night and absolutely the best (even better than what I had when I was on that other OS).  My only hesitancy is that it asked for my password.  I know it has to have it to be able to function but that's why I normally stick with an extension from the original provider (Google in this case).  My paranoia may be unfounded but that's because I don't know how this works.  Kind of like granting all of these permissions when you download an app to your phone.

---

### Post by Oldhacker on 2012-05-20
As I said earlier in this thread, gm-notify is the best gmail notifier for ubuntu and sounds like what you want. It notifies immediately on new email, not by polling like most(/all?) other notifiers. It outputs a configurable audio sound, and **it lights a static mail icon indicator which stays lit while you have unread google email** (although that indicator only works in Unity, not gnome-shell unfortunately).

That is the only element that seems to be missing in my installation now. For me, the indicator does not remain visible for more than ten seconds - and I am using Unity. Have I missed something else in my installation of gm-notify?

---

### Post by unibroker on 2012-05-20
> **Oldhacker said:**
> As I said earlier in this thread, gm-notify is the best gmail notifier for ubuntu and sounds like what you want. It notifies immediately on new email, not by polling like most(/all?) other notifiers. It outputs a configurable audio sound, and **it lights a static mail icon indicator which stays lit while you have unread google email** (although that indicator only works in Unity, not gnome-shell unfortunately).

That is the only element that seems to be missing in my installation now. For me, the indicator does not remain visible for more than ten seconds - and I am using Unity. Have I missed something else in my installation of gm-notify?
The envelope icon in the top right corner should change to a blue color when you have something new in your inbox and remain that way until you open it.  Go to System Settings, Details, Default Applications and see what you selected under Mail.

---

### Post by Oldhacker on 2012-05-20
Gnome Gmail is my default mail application.

Also, I have checked Gmail Web Interface, the same as yours. The only difference that I see is that you are using Chromium and I am using Firefox.
Perhaps that is Google's revenge for not choosing their browser. ;-)

---

### Post by unibroker on 2012-05-20
> **Oldhacker said:**
> Gnome Gmail is my default mail application.
Mine is Chromium Web Browser same as that listed under Web.  What are your choices in the pulldown menu under Mail?  Interesting you see the notification for a brief time but don't see the icon color change.  Also, just checked my gm-notifier configuration and "Gmail webinterface" is selected under Account (not "Current default mail client").

---

### Post by Oldhacker on 2012-05-20
My mail choices are "KMail Service" and "Gnome Gmail"

Those are the only ones.

---

### Post by Oldhacker on 2012-05-21
[SIZE="2"][FONT="Verdana"]I tried the last thing that I could think of to make the notify message remain until acknowledged. I not only installed Chromium, but set it as the default browser. The results were identical to when I had Firefox as the default browser. The notify message appears for a few seconds and then goes away. I might as well go back to Firefox as the default browser since it feels more familiar to me.[/FONT][/SIZE]]

---

### Post by unibroker on 2012-05-21
> **Oldhacker said:**
> [SIZE="2"][FONT="Verdana"]I tried the last thing that I could think of to make the notify message remain until acknowledged. I not only installed Chromium, but set it as the default browser. The results were identical to when I had Firefox as the default browser. The notify message appears for a few seconds and then goes away. I might as well go back to Firefox as the default browser since it feels more familiar to me.[/FONT][/SIZE]]
I am sorry for your trouble. I searched quite a bit yesterday for how to add to that drop down menu in Mail setting and came up empty (even posted on another board where I'd been previously successful getting advice).  I never edited that menu and was surprised that Chromium browser was listed as my default Mail.  The only other thing I can think of is I used Thunderbird as an email client with Gmail for awhile but decided to uninstall it.  Quite possibly when I initially installed Thunderbird the default Mail menu was modified during configuration.

Good luck.

Just went to the Ubuntu Software Center and they had a link to the Developer's website.  You have to have an account with Launchpad in order to ask questions.  [https://launchpad.net/gm-notify]("https://launchpad.net/gm-notify")

---

### Post by Oldhacker on 2012-05-21
I am somewhat embarassed as well as appreciative that I have gotten so many responses to my post.
It is not really that important to have something that fulfills all of my wishes. There would be no further development on anything if version 1.0 contained everything that all people desired.
The popup reminder that I have learned about from this thread is already much better than when I had nothing except to periodically go into Gmail to see if there was any mail there for me.

Thanks again to all ---

---

### Post by paulkiss on 2012-07-15
Thanks a lot guys. gm-notify is EXACTLY what I've been looking for. Yahoo!

---

### Post by madeinfamous on 2012-07-16
Allo,

hum... this is the one...

sudo apt-get install unity-mail

[see pic]("https://plus.google.com/photos/111987164838983449652/albums/posts/5730109869591188450")

cheer's

---

### Post by ales004 on 2012-12-06
Install unity-mail and it's perfect. Thanks!

---

