---
title: "Import e-mails from Outlook"
date: 2005-08-19
forum: Desktop Environments
---

### Post by sx460 on 2005-08-19
Hello,

I'm currently on Windows but would like to switch to Ubuntu. My e-mails are held in Outlook, how can I import them into Evolution? Is this possible or do I have to forget about all my old e-mails? Thanks!

---

### Post by tahuya_rat on 2005-08-19
Try this thread:

[Import Outlook](http://ubuntuforums.org/showthread.php?p=279759#post279759) 

HTH

-tahuya_rat

---

### Post by grim42 on 2005-08-19
It's a bit involved ... The following is quoted from Evolution help.
> 
Migrating Local Outlook Mail Folders

Exchange and IMAP mail is stored on the server, so you do not need to migrate it to your Linux partition. However, if you have stored mail on your computer, you might want to make it accessible to Evolution.

First, while using Windows, prepare your messages for import:

   1.

      Clean up your mail. Delete messages and folders you do not need, and click File > Folders > Properties > Advanced > Compact to erase old, deleted messages from your PST file.
   2.

      If you nest your folders one inside another, you might want to rename subfolders so that you can tell which folder they belong to. You must re-nest them after you load them into Evolution.
   3.

      Import the files into Mozilla Mail (or another mailer, such as Netscape or Eudora, that uses the standard mbox format). Linux mailers cannot do this task, because it requires a library available only under Windows. In Mozilla, import by selecting Window Mail & Newsgroups Tools Import.
   4.

      Mozilla creates a set of files in the directory Windows\Application_Data\Mozilla\Profiles\(UserName)\(Random Letters)\Mail\Local Folders\OutlookMail\. The data files are those that have no file extension.

      If you are using Windows XP or Windows 2000, your Windows hard drive is probably in the NTFS format, which some Linux systems cannot read without additional software. You might find it simpler to copy the mail folders to a different drive or to burn a CD.

When you have your mail in a format Evolution can understand, reboot to Linux. Then continue with the following procedure. To create new folders for your files:

   1. Mount your Windows drive or the disk where you saved the mail files.
   2. Copy all the mail files into your home directory or another convenient place.
   3. Start Evolution.
   4. Press Shift+Ctrl+F or select File > New Folder to create the folders you want. 

To import the data files:

   1.

      In Evolution, open the File Import assistant by clicking File > Import.
   2.

      Click Next, then select Import A Single File.
   3.

      Leave the file type as Automatic, then click Browse to select the data file.

      Remember, the data files are the files that have no file extension.
   4.

      Select the folder where you want to put the imported data file.
   5.

      Click OK.
   6.

      Repeat the import steps until you have imported all your mail.


---

### Post by crispingatiesa on 2005-08-19
you have to export the e-mail as .pst (personal folders from Outlook)
 and then import them using Mozilla Thunderbird for linux to import the messages because as far as I know Evolution doesn't read .pst files. Then, you have to re-export the mails from Thunderbird into a file type that Evolution reads.

The second step  I can't tell you what kind of file type is because I'm sitting in a windows workstation now.

If you haven't found how I'll check later.

Good luck

---

### Post by sx460 on 2005-08-19
Thanks for the great info! This should be very simple and straight forward.  Thanks again :)

---

### Post by outlook on 2005-08-30
I have been using it. I'll suggest you [outlook express missing folders ](http://www.oemailrecovery.com/outlook-express-fix.html) and [recover dbx](http://www.mail-repair.com/dbx-fix.html)

---

### Post by BluBoy on 2005-08-30
Is  there anything that will work with Thunderbird?

Thanks!

--
BluBoy

---

### Post by derheinrich on 2005-09-08
If you've got loads of subfolders to import and don't want to use the interactive Evolution import menu, do this:

Import the Inbox textfile to (you guessed it) -> Inbox.

Create one subfolder under Inbox (or perhaps import the first subfolder-textfile).

Evolution will create the folder  /home/{your_name}/.evolution/mail/local/Inbox.sbd

Then copy all the Mozilla subfolder-textfiles (the ones without the .msf ending) into the folder above. 

Kill any running Evolution processes and restart Evolution.

The copied files should now represent subfolders under your inbox.
The first time you select a subfolder Evolution automatically generates the index-file in the background and everything's perfect!

This saved me hours!

---

### Post by wildthing-zim on 2005-09-08
thanks guys this is great BUT what can i do with my txt file address book or csv or wab , how can i get my addresses into evolution ??

---

### Post by derheinrich on 2005-09-09
I installed kaddressbook with all the libraries necessary to run it under gnome. It has great interface which shows you the contents of the csv-file so you can join the csv-fields to the internal field-descriptors of kaddressbook easily. 

Once you're finished with importing you can then export your addresses to .vcf again, which is the format that Evolution understands.

If you're not from an english-speaking country then this is the only way this is possible (afaik) since all those perl and ruby scripts need english field-descriptors to generate the vcf-file automatically and cannot handle foreign ones which is what you get when you generate your csv-file with a german or french Outlook-version.

---

