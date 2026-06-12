---
title: "Special email script: Is this even possible?"
date: 2009-03-18
forum: Desktop Environments
---

### Post by Maconvert on 2009-03-18
Hello,

I'd like to be able to set up an email program on Ubuntu that will look for a specific subject and, if it finds it, it will save all of that email's attachments to a specified folder.

Has anyone done something like this or know if it can be done?

Please let me know.

Cheers.

---

### Post by lovinglinux on 2009-03-18
I know a solution if you want to extract attachments from received e-mails. I have been successfully using this method with a Gmail account.

Just let me know if this is what you want and if a Gmail account setup would be viable, then I will explain to you.

---

### Post by Maconvert on 2009-03-18
Yes!!!
That's what I want.
I want the email program to frequently check (every 2 to 5 minutes) my Gmail account and, upon downloading an email with a specific subject line, it would take all the attachments from that email and save them into a folder on my hard drive.

If I can get that to work it will be AWESOME!!!

Thanks very much!

---

### Post by lovinglinux on 2009-03-19
> **Maconvert said:**
> Yes!!!
That's what I want.
I want the email program to frequently check (every 2 to 5 minutes) my Gmail account and, upon downloading an email with a specific subject line, it would take all the attachments from that email and save them into a folder on my hard drive.

If I can get that to work it will be AWESOME!!!

Thanks very much!

We are going to use a shell script to do this. 

In order to allow the script to get the attachments from Gmail messages we need to download a copy of the e-mails to a local folder. We do this with offlineimap and GMail IMAP support. 

Open the Gmail account then go to "Settings", select the "Forwarding and POP/IMAP" tab and enable IMAP. Save it.

We also need to create a filter to detect the desired subject and label it accordingly. So, select the "Filters" tab and click "Create a new filter". In the pop up window type the specific word you want to detect in the "Subject" field. I will use the word **mykeyword**, because it will need it again in the script. Then click "Next step", select "Skip the Inbox (Archive it)" and "Apply the label:" >>> "Choose label" >>> "New label..." and type  **mykeyword** in the "New label" field. Click OK and then "Create Filter".

Now download the required applications by running the following command in the terminal:

```
sudo apt-get install offlineimap mpack
```

Now create a folder to store the e-mail messages locally. I will use **~/mail** (i.e. /home/username/mail), because we will need this path for the script too. You can change it if you want, but if you do so, make sure you change the path in the script and in the offlineimap config.

Now we need to configure the offlineimap application. Run the following command to open the config file with the text editor:

```
gedit ~/.offlineimaprc
```

Add the following code to the file and save it.

```
[general]
accounts = GMail

ui = Noninteractive.Basic

[Account GMail]
localrepository = GMailLocalMaildirRepository
remoterepository = GMailServerRepository

[Repository GMailLocalMaildirRepository]
type = Maildir
localfolders = **~/mail/**

[Repository GMailServerRepository]
type = IMAP
remotehost = imap.gmail.com
remoteuser = **[COLOR="Red"]yourmailaddressatgmaildotcom[/COLOR]**
remotepass = [COLOR="Red"]**yourmailpassword**[/COLOR]
ssl = yes
```

[COLOR="Red"]**Don't forget to replace the info in red with your gmail account login info.**[/COLOR] If you use a different folder than **~/mail**  then you need to change it here and in the shell script.

To sync your Gmail account with the local copy just run the following command:

```
offlineimap
```

Check if your messages and folders were downloaded to the **~/mail** directory. [COLOR="Red"]**DON'T DELETE THEM! IF YOU DELETE THEM, YOUR MESSAGES WILL BE ALSO DELETED IN THE GMAIL SERVER IN THE NEXT SYNC!**[/COLOR]

Now we need to create a script to download and extract the attachments:

```
#!/bin/bash

offlineimap && 
munpack -C $HOME/[COLOR="Red"]**[B]destination_folder**[/B][/COLOR] $HOME/mail/**[COLOR="Red"]mykeyword[/COLOR]**/new/* && 

```

Where:

*$HOME/destination_folder* is the destination folder where the attachments will be saved under the user home directory

*$HOME/mail/mykeyword/new/** is the local path to any messages (*) filtered by Gmail with the label **mykeyword**. The *$HOME/mail* path is the mail folder under the user home directory that we created before.

It is advised to delete the original message after extracting the attachments, otherwise it will be download again and again. To do this add the following code to script above

```
rm -f $HOME/mail/[COLOR="Red"]**mykeyword**[/COLOR]/new/* && offlineimap
```

This will delete the local copies of the messages containing mykeyword in the subject and will resync the Gmail account to delete them on the server.

Save the script as something like **gmail-extractor.sh**, then access it properties and make sure you can execute it as program. Then simply execute the script.

Basically the script will do this:

1 - Sync the messages and folders from the Gmail account with a local copy in the /home/username/mail folder

2 - Extract the content of the new message with the **mykeyword** label to the /home/user/destination_folder. 

3 - Delete the local copy of the downloaded messages and sync with Gmail again to delete them in the server.

EDIT: to make this process automatic, you can create a cron job to run the script in regular intervals. If you don't know how to do this, you can install *gnome-schedule*, which is an easy GUI for cron jobs.

---

### Post by Maconvert on 2009-03-19
Very, very cool!

I won't get a chance to try this until Saturday or Sunday though because the wife and I are going to Harrison Hot Springs for the next couple of days. Once I get this working I will be able to email ".torrent" files from anywhere in the world and have them transferred to my Deluge "Auto" watched folder. Deluge will then grab them and start downloading the associated files that the torrents point to.

I'm looking forward to getting this working.

Cheers!

---

### Post by lovinglinux on 2009-03-19
> **Maconvert said:**
> Once I get this working I will be able to email ".torrent" files from anywhere in the world and have them transferred to my Deluge "Auto" watched folder. Deluge will then grab them and start downloading the associated files that the torrents point to.

Yes, you can. Since you will sending e-mails to yourself and will extracting only torrent attachments, I recommend two more steps.

1 - instead of [COLOR="black"]**mykeyword**[/COLOR] label/subject use a string of characters like a password in the subject, to avoid eventually extracting files from spam or other message containing the keyword in the subject.

2 - instead of

```
munpack -C $HOME/[COLOR="Red"]**destination_folder**[/COLOR] $HOME/mail/mykeyword/new/* &&
```

use this

```
munpack -C $HOME/[COLOR="Red"]**temp_folder**[/COLOR] $HOME/mail/mykeyword/new/* &&
mv $HOME/[COLOR="Red"]**temp_folder**[/COLOR]/*.torrent $HOME/[COLOR="Red"]**watched_folder**[/COLOR]/
```

This will prevent the script form extracting unwanted files to the deluge's watched folder. When you extract the attachments from the e-mail messages, the script will also extract the message itself and save it as **message.desc**. So with this code you will extract them to a temporary folder and move only the torrent files to the watched folder.

---

### Post by Maconvert on 2009-03-19
Hello,

I will incorporate the changes you’ve suggested.
However, because I will be creating a new Gmail account that will only be used for this purpose (never given out to anyone) I doubt I will get any spam.
Gmail’s filters are pretty good as it is. My regular Gmail account rarely ever gets any spam.
In regards to stripping out only the “.torrent” files, it probably won’t be necessary because the only attachments that this account will likely ever receive will be this type of file. However, I think I’ll keep it just in case I want to send something else to my house to check out later.

Anyway, thank you very much for helping me out with this. Hopefully it will go smoothly and I won’t need to post again for help. 

Cheers!

---

### Post by lovinglinux on 2009-03-19
> **Maconvert said:**
> Hello,

I will incorporate the changes you’ve suggested.
However, because I will be creating a new Gmail account that will only be used for this purpose (never given out to anyone) I doubt I will get any spam.
Gmail’s filters are pretty good as it is. My regular Gmail account rarely ever gets any spam.
In regards to stripping out only the “.torrent” files, it probably won’t be necessary because the only attachments that this account will likely ever receive will be this type of file. However, I think I’ll keep it just in case I want to send something else to my house to check out later.

Anyway, thank you very much for helping me out with this. Hopefully it will go smoothly and I won’t need to post again for help. 

Cheers!

You are welcome.

Having a dedicated Gmail account is the best way to go. I also have one just for this procedure. Nevertheless, munpack will extract not only attachments, but the message itself. It shouldn't be a problem to extract it to the watched folder, because deluge only recognize torrent files, but I like to keep things clean ;)

If you find any problems just post here and I will be glad to help you. Good luck.

---

