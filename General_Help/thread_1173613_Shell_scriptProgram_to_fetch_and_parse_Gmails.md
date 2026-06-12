---
title: "Shell script/Program to fetch and parse Gmails"
date: 2009-05-29
forum: General Help
---

### Post by timo1023 on 2009-05-29
I would basically like to be able to send emails to a certain gmail address and have my computer fetch them and do certain things based on the content of the email. For instance, an email with "p" as the subject would play/pause music. And so on and so forth. 

The problem I am running into is easily fetching and storing the emails as text files. I am trying fetchmail and mutt, but I am having trouble. Is there an easier way to do this? Also, I need some way to keep checking the email address ever few seconds/minutes: how would I do this?

Thanks.

---

### Post by lovinglinux on 2009-05-30
I have a method, but it is a little bit complicated, so it will take some time to write a tutorial for you.

*EDIT: the tutorial is already and available in the next post.*

Basically you will use cron to periodically sync the gmail account locally using offlineimap, which is a command-line IMAP synchronization tool. Then you will need a script to check the existence of the mail with the desired function in the subject and perform the command you want if the file is found.

BTW, I used this method in the past to remotely activate my TV recorder by e-mail. I could setup the start time, date and channel with a little bit more complicated script 8)

---

### Post by lovinglinux on 2009-05-30
Tutorial:

Just for reference, **~/** means your user home folder. So **~/Pictures** is your personal Pictures folder. This way I don't have to write **/home/yourusername/** all the time. While we can use **~/** in scripts and commands most of the time, sometimes it doesn't work, so I will use only **$HOME** in the code, which is basically the same thing but should work properly.

My tutorial will save the scripts in the **~/bin** folder, but you can use any other directory you use to save scripts, as long as you replace all **~/bin** paths with the appropriate paths. I'm assuming you know how to make a script executable, so I will skip these during the tutorial.

This method work better if you have a separate Gmail account just for this, because it will download all messages in the account to your computer, so if you have huge files attached to some e-mails it could take too much time to download them and this could interfere with the pipeline of this tutorial.

So, first you need to create a **~/gmail** folder to store the Gmail messages locally. Then install *offlineimap* by running the following code:

```
sudo apt-get install offlineimap
```

Then create the offlineimap configuration file in your home folder:

```
gedit ~/.offlineimaprc 
```

Add the following code to it and save it:

```
[general]
accounts = GMail

ui = Noninteractive.Basic

[Account GMail]
localrepository = GMailLocalMaildirRepository
remoterepository = GMailServerRepository

[Repository GMailLocalMaildirRepository]
type = Maildir
localfolders = [COLOR="Red"]**~/gmail/**[/COLOR]

[Repository GMailServerRepository]
type = IMAP
remotehost = imap.gmail.com
remoteuser = [COLOR="Red"]**yourgmailaccount**[/COLOR]@gmail.com
remotepass = [COLOR="Red"]**yourgmailpassword**[/COLOR]
ssl = yes

```

Change the values in red to match your account and paths.

Then go to your Gmail **Settings**, select the **Forwarding and POP/IMAP** tab and enable IMAP. Save it.

Then run the following command to sync the Gmail account with your local folder:

```
offlineimap
```

Check if your messages and folders were downloaded to the **~/gmail/** directory. [COLOR="Red"]**DON'T DELETE THEM! IF YOU DELETE THEM, YOUR MESSAGES WILL BE ALSO DELETED IN THE GMAIL SERVER IN THE NEXT SYNC!**[/COLOR]

Now we need to create a filter that will put each message on a specific mail folder according to the subject. Go to your Gmail account, click **Settings** then select the **Filters** tab and click **Create a new filter**.

In the pop up window type **play** in the **Subject** field. Then click **Next step**, select **Skip the Inbox (Archive it)** and **Apply the label:** >>> **Choose label** >>> **New label...** and type **play** in the **New label** field. Click OK and then **Create Filter**.

To test if the filter is working, send a message to yourself with the subject **play**, then open the **All Mail** folder and check if the message is there with a **play** label. 

Since we created this filter and configure it to be archived, any messages with the subject **play** will be downloaded to **~/gmail/play/new** folder when you run offlineimap.

Now we need to create a script to sync the Gmail account, then execute the desired command if the message with the specific command exists.

```
gedit ~/bin/gmail.sh 
```

and add the following code to it

```


#!/bin/bash

offlineimap &&

PLAY=$(ls $HOME/gmail/play/new/ | wc -l)  

if [ ${PLAY} = "0" ]; then

exit

else

zenity --info --text "The thing is working. This is a placeholder for the command you want to execute when the script finds a message with play in the subject"

rm -f $HOME/gmail/play/new/*

offlineimap &&

exit

fi

```

Don't forget to change the permission of the script to allow it to run as program.

Now we need to setup the cron job to run the script **~/bin/gmail.sh** every 5 minutes or less, according to your preferences.

1 - Type the following command in the Terminal to create a file named .change.cron

```
gedit ~/.change.cron
```

2 - Add the following lines to the file, replacing "[COLOR="Red"]**/home/you/**[/COLOR]" with your user path.

```

USER=[COLOR="Red"]**you**[/COLOR]
HOME=[COLOR="Red"]**/home/you**[/COLOR]
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin:/home/[COLOR="Red"]**you**[/COLOR]/bin
DISPLAY=:0.0
MAILTO=[COLOR="Red"]**you**[/COLOR]

00,05,10,15,20,25,30,35,40,45,50,55 * * * * $HOME/bin/gmail.sh >/dev/null 2>&1

```

This is how a cron job is layed out:

minute (0-59), hour (0-23, 0 = midnight), day (1-31), month (1-12), weekday (0-6, 0 = Sunday), command

This cron job will launch the ~/bin/gmail.sh script every 5 minutes.

No go to **System** > **Preferences** > **Startup Applications** (aka Sessions) and add a startup program like the one below. Don't forget to replace **/home/you/** with your user home path.

> Name: Cron Changer
Command: crontab /home/[COLOR="Red"]**you**[/COLOR]/.change.cron
Comment: Will add jobs to cron

Run the following command to update the cron:

```
crontab /home/[COLOR="Red"]**you**[/COLOR]/.change.cron
```

then check if the cron job was added by running the following command:

```
crontab -e
```

That's it. Now send a message to your gmail account with the subject play and wait to see the result.

---

### Post by timo1023 on 2009-05-30
What a wonderful tutorial: thank you very much. I changed your script a little to fit my needs, but I have run into a rather frustrating obstacle. Basically I use my phone to send a text message to my gmail address. It gets filtered yada yada and I extract the 4th from last line of the file and use that to figure out the desired command. Right now I am just using "p" for the command "quodlibet --play-pause", i.e. to play and pause my music (from afar--heh).

The script runs wonderfully by hand, i.e. "sh ~/bin/gmail.sh", but the cron job fails on the
```
if [ "$desiredcommand" = "p" ]
```
check (I get the "fail" zenity message). The entire program is shown below.
```
#!/bin/bash

offlineimap &&

PLAY=$(ls $HOME/gmail/play/new/ | wc -l)  

if [ ${PLAY} = "0" ]
then
	zenity --info --text "0 ????"

	exit
else
	filename=$(ls $HOME/gmail/play/new | awk '{print $1}' | head -1)
	lines=$(($(wc -l $filename | awk '{print $1}')-4))
	desiredcommand=$(sed -n "$lines p" $filename)

	if [ "$desiredcommand" = "p" ]
	then
		quodlibet --play-pause
	else
		zenity --info --text "FAIL: ${desiredcommand}"

	exit
	
	fi

	#delete if necessary; commented out for testing
	#rm -f $HOME/gmail/play/new/$filename
	offlineimap &&

	exit
fi
```

I can't think of a reason why the check would fail with the cron job and not with the manual start. Any thoughts?

---

### Post by lovinglinux on 2009-05-30
> **timo1023 said:**
> I can't think of a reason why the check would fail with the cron job and not with the manual start. Any thoughts?

I don't know. I have trouble with conditions myself, no matter how hard I try. That's why I used counter to check if the ls command returns a "0" or not.

---

