---
title: "Hiding the installation folder of an application"
date: 2011-02-19
forum: Desktop Environments
---

### Post by king13 on 2011-02-19
I have an application installed under the directory /home/ubuntu/MyApplication

I have a symbolic link on the desktop to a launch.sh script inside the MyApplication directory

Launch &#8594; /home/ubuntu/MyApplication/launch.sh

I have ubuntu(10.10) running on a usb flash drive. I want to allow other user's to run the application by using the link on the desktop but I want to keep the installation folder private. So the users can run the application but they are unable to view or copy the files inside the installation folder.

Any ideas or suggestions are more the welcome 


Thanks,

El

---

### Post by Hippytaff on 2011-02-19
Hi and welcome to the forums

You can hide files (and folders) by renaming them with a full stop/period before the name ie .filename thus```
mv filename .filename
``` where filename is the name of the file

There will be some hidden files like this in your home folder. Open a terminal and do ```
ls -a
``` to view them.

Don't know what you mean by installation folder though. If you change the name of a folder the programme needs to access, this will cause problems running the programme.

---

### Post by king13 on 2011-02-19
thanks for the reply

I am running ubuntu from a usb stick

i have an application installed under the directory /home/ubuntu/MyApplication

i have created a symbolik link from the desktop which calls the script that launches the application. The script is under /home/ubuntu/MyApplication/launch.sh

Now what i am trying to achieve is allow other users to run the application by using the symbolik link, but i dont want them to be able to view or copy the content of /home/ubuntu/MyApplication, which contains some important application files.

The other users will also have access to the usb stick

Thanks,

---

### Post by Hippytaff on 2011-02-19
ok...so do the .file period thing but you need to be aware that you need the package to know that that's what you've done. If you wrote the script/package then you can edit it, else, like I said, if the programe needs that folder for whatever reason then you need to tell that programe of the change...somehow

---

### Post by king13 on 2011-02-19
My concern now is that the users can see where the symbolic link is pointing to and then navigate to the hidden folder and view or copy the files. Do you know if there is a way of encrypting the application folder which will guard from someone copying the content but at the same time allow a user to call the launch script through a shortcut on the desktop?

---

### Post by Hippytaff on 2011-02-19
[This]("https://help.ubuntu.com/community/EncryptedPrivateDirectory") might be worth a read

---

### Post by asmoore82 on 2011-02-19
> **king13 said:**
> I have ubuntu(10.10) running on a usb flash drive. I want to allow other user's to run the application by using the link on the desktop but I want to keep the installation folder private. So the users can run the application but they are unable to view or copy the files inside the installation folder.

Are those files necessary for the application to run?

If not, separate them from the application.

If so, that is a paradox — you can't let them run an application
if you refuse to give them what's necessary to do so.

---

### Post by deconstrained on 2011-02-19
I do this all the time.

Make a directory ~/.alt or ~/.(something) and a subdirectory (for example) ~/.alt/bin

Then, put in your ~/.bashrc:
```
export PATH=$PATH:$HOME"/.alt/bin"
```

Then, when you install something, the configure file will often have an option such as --prefix or --exec-prefix. You want to pass the path to this directory to that option flag, and then when you run 'make install', the executable will install to that directory and you can launch it like any other program.

And one more thing
> **king13 said:**
> My concern now is that the users can see where the symbolic link is pointing to and then navigate to the hidden folder and view or copy the files. Do you know if there is a way of encrypting the application folder which will guard from someone copying the content but at the same time allow a user to call the launch script through a shortcut on the desktop?
Encryption is both overkill and impractical for doing this sort of thing. Also, if you have the folder encrypted but it is group readable/executable, **then it doesn't matter that it's encrypted; it's decrypted in the userspace and other people can still read it.** What you want to do is change the *group permissions and group ownership* of the directory to your liking.

What you could do is make the files and containing folder group-executable, and the files group-readable, but not the folder readable. That way people could not view a directory listing but they could still get access to the relevant files.

You'd only use encryption to prevent someone with physical access to your computer (if your computer has no BIOS password) from reading the data, because that person can use a live OS disk to bypass the permissions. However, if there are users logged into your machine remotely by SSH, VNC or some other means, setting the permissions and group ownership of the folder so that people can only see what you want them to is the proper way of protecting the folder.

---

### Post by king13 on 2011-02-20
very helpful comments, thanks for your time guys

---

