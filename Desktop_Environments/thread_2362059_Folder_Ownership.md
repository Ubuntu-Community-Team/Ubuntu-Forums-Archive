---
title: "Folder Ownership"
date: 2017-05-23
forum: Desktop Environments
---

### Post by jasemon on 2017-05-23
I would like to change the owner of my folder for the Raspberry Pi Wordpress LAMP project so I can insert the required file to utilize my Apache server.  Can anyone help me edit owner on a folder please?

---

### Post by QIII on 2017-05-23
You probably do not want to change ownership of any directories.  You would likely foul up the entire works.  The owner of the site's directories, for instance, needs to be www-data (or whatever is appropriate for your configuration).  Other directories are owned by root.

What file to you need to move where and what trouble are you having?

---

### Post by jasemon on 2017-05-23
The file is wp-config.php. It is recommended to create this file and fill in some information via a editor after copy and pasting the contents of the wp-config-sample.php file.  I have succeeded editing the file but the folder it needs to be housed in will not let me insert the file.

---

### Post by QIII on 2017-05-23
Please explain "will not let me insert the file".  Are you getting a message to the effect that you do not have permmission to do that?

Would you please paste the exact command you are using and the exact message you are receiving?

---

### Post by jasemon on 2017-05-23
When moving the file into the folder the explaination for the error message in detail is "Error while moving the file into /var/www/html" further details pertaining to the error are "Error moving file: Permission denied". Title of the message is "Error while moving "wp-config.php""

---

### Post by QIII on 2017-05-23
How were you attempting to move the file?  A GUI file manager or via the terminal?

---

### Post by jasemon on 2017-05-24
A GUI file manager standard with ubuntu.

---

### Post by howefield on 2017-05-24
If you are not too afraid of the command line, you could try..

```
sudo -u www-data cp /home/Documents/wp-config.php /var/www/html/
```

I'm guessing at the source paths given what you say above, so if they are incorrect you can amend to suit, likewise if the owner of the destination folder is not www-data.

Are you using ssh to access the pi or do you have direct access ?

---

### Post by jasemon on 2017-05-24
Ok, I am starting to understand.  I do not know what ssh is.  Can you tell me what the command line is if the file is on the desktop?  The command line above did not work with the file in the Documents folder.

---

### Post by QIII on 2017-05-24
Hello again.

Could you explain what you meant by "did not work"?  We aren't trying to be obtuse.  We can't see what you are seeing and we need detailed information to help you.

When you use the command line, you get messages when things "don't work".  If you cut and paste those messages here, we can better understand what is going on.  This is why we generally ask people to use the terminal.

---

### Post by jasemon on 2017-05-26
The following message appears in the terminal:

cp: cannot stat '/wp-config.php': No such file or directory

---

### Post by Dennis N on 2017-05-26
> cp: cannot stat '/wp-config.php': No such file or directory 

This file would be in the root directory. Are you sure that's the right location? If you want your home folder:

use **~/wp-config.php**

---

### Post by jasemon on 2017-05-26
Objective accomplished!! Thank you.

---

