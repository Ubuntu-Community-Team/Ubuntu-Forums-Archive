---
title: "keep root powers in console without needing sudo"
date: 2009-04-11
forum: General Help
---

### Post by CynicalPsycho on 2009-04-11
how do I maintain root priviliges at the console without having to keep using sudo?

---

### Post by _Purple_ on 2009-04-11
If you have enabled your root account, then you can do so by typing su in terminal but its not a good idea. Using sudo should give you enough time to accomplish any task.

---

### Post by holiday on 2009-04-11
I go

$ sudo su

and type in my user password

I get a root shell

It's a fine idea. People have this fear like letting the kids out after dark. 

Ooooh - you might do something bad. 

But if you're smart enough to do something bad then it's not likely you're going to.

---

### Post by lisati on 2009-04-11
It's like a "power toy" that assumes you know what you're doing. Caution is advised!!!!!

---

### Post by ibuclaw on 2009-04-11
May I just say that you **do not** need to create a password account for root.

```
sudo -s
```
Is all the steps that is required for you to do.

Alternatively, if you use a small set of applications most commonly, then you can set up the sudoers file to allow certain programs to run without the need for a password.

Regards
Iain

---

### Post by CynicalPsycho on 2009-04-11
> **tinivole said:**
> May I just say that you **do not** need to create a password account for root.

```
sudo -s
```
Is all the steps that is required for you to do.

Alternatively, if you use a small set of applications most commonly, then you can set up the sudoers file to allow certain programs to run without the need for a password.

Regards
Iain
how do you do this?

---

### Post by CynicalPsycho on 2009-04-11
thanks for all the replies guys, you've all been quite helpful... cept that one guy stating the obvious.... bout power toys or w/e...

---

### Post by ibuclaw on 2009-04-12
> **CynicalPsycho said:**
> how do you do this?
For reference on how to setup your sudoers, I suggest you have a skim through this guide: [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)
It may need a little work here or there (I should know, I wrote some bits of it), but should give you enough information to get some small things started.

But to give you the dropdown basics. Sudo's configuration file is located in /etc/sudoers. But due to the powerness of the program, we don't want to edit it directly in the event of a type error in file; so we use the program **visudo** instead. visudo is a program which sanity checks the file after you've finished writing it.

[SIZE="4"]**Opening Sudoers**[/SIZE]
visudo, as of Intrepid, uses the sensible-editor to edit the sudoers file. So to ensure that sensible-editor is setup to your preferences run:
```
sudo select-editor
```
And you'll be given a list of programs to choose from. In most cases, you'll want to choose **nano**.

Which that all ready to go, launch visudo.
```
sudo visudo
```
and you are in.

[SIZE="4"]**Hello Configuration!**[/SIZE]
For example purposes, lets tweak the sudo permissions for **apt-get**.
Now, scroll to the bottom, and we can insert our line:
```
%admin ALL=(ALL)NOPASSWD:/usr/bin/apt-get
```
To break it down:
[LIST]
[*] **%admin** - All users of the admin group
[*] **ALL=**   - from any IP address
[*] **(ALL)** - can run as any user
[*] **NOPASSWD** - with no password required
[*] **:/usr/bin/apt-get** - the list of comma, separated, applications.
[/LIST]

**Note:** sudo reads the sudoers file and applies permissions in order from top to bottom. So the last line in the file will overwrite any previous conflict with the config settings. So it is best to put new configuration lines at the bottom.

[SIZE="4"]**Fine Graining Permissions**[/SIZE]
Now, as quick and efficient this may be in most cases, it's not the best thing to do from a security point of view for a number of reasons:

**1. **Any connected computer can run the command, so long as they are logged in as one of the administrators. From a paranoid perspective, ideally we would rather only computers within our local network/subnet.

**2. **They can run the given command as any user. Which apt-get isn't intended for. (Although the argument is weak in this case, in some scenarios and with certain applications, you could be quite literally giving a key for a user to invade another user's private account if not careful).

**3. **Sometimes, we want the user only to be able to perform "**certain**" tasks of the application, and not all features.

**4. **In some circumstances, we only want **one user** to run a command, rather than all the users in the admin group.

Considering this list, you can make the following changes to it.

1)** Restrict Computers**
```
%admin **192.168.1.0/255.255.255.0**=(ALL)NOPASSWD:/usr/bin/apt-get
```
192.168.1.0 is the IP of your local network.
255.255.255.0 is the subnet of your local network.

So, in this instance, you are restricting the use of sudo only to users with an IP address of 192.168.1.1 through to 192.168.1.254

2)** Restricting User Switching**
```
%admin 192.168.1.0/255.255.255.0=**(root)**NOPASSWD:/usr/bin/apt-get
```
They can only run the given commands without a password as root. Doesn't matter how hard they try otherwise. ;)

**Note:** if a previous permission is set so the user can run the command as any user.
More specifically this line that is the default in Ubuntu:
> # Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
Then they will have to provide their own password to continue.

A more secure method:
> # Members of the admin group may gain root privileges
%admin ALL=(root) ALL
Where they will be instead denied if they try to run an application as another user.

3)** Restricting Application Usage**
```
%admin 192.168.1.0/255.255.255.0=(root)NOPASSWD:**/usr/bin/apt-get update,/usr/bin/apt-get upgrade**
```
And now, they can only manually update the sources and upgrade the system. Everything else (install, remove, dist-upgrade) is denied!

4)** Restricting use of sudo to Single Users**
```
**tinivole** 192.168.1.0/255.255.255.0=(root)NOPASSWD:/usr/bin/apt-get update,/usr/bin/apt-get upgrade
```
And now, only I can run 'apt-get update' and 'apt-get upgrade' from a local computer on the system.


This is just the icing on the cake for the level of fine tuning you can do in the sudoers file.


[SIZE="4"]**Conclusion**[/SIZE]
For the most generic solution in this example, I recommend:
```
**tinivole** ALL=(root)NOPASSWD:/usr/bin/apt-get
```
Since I'm the only admin on my computer, I'd rather just specify my own username, just incase...
For the paranoid:
```
**tinivole** 192.168.1.0/255.255.255.0=(root)NOPASSWD:/usr/bin/apt-get
```
NOTE: Use your username in place of 'tinivole', you don't want to give **me** access to your system. :twisted:

[SIZE="4"]**Extras**[/SIZE]

5)** Restrict Applications**
There is a hidden 5th that I forgot to mention. In some cases, you want to restrict the application once it has been given root powers.

ie: **vim** allows you to shell out of the editor and run commands using the **!** operator, as an example:
```
:!ls
```
The risk? If given the permissions to running vim as root, you can carry out any administrative task on the system. Which isn't very good if you just want certain users to run vim as root, but not any other command.

For this, we have the **NOEXEC** option, with will prevent the command from shelling out.
```
%admin ALL=(root)NOPASSWD:**NOEXEC**:/usr/bin/vim
```
Although, bare in mind that for the majority of applications, this isn't the best option for usability, since programs such as '**apt-get**' do indeed fork a shell to run applications such as **dpkg** and **wget**.


**[SIZE="3"]Remember, as the user of your own system, you are advised to use your powers responsibly.[/SIZE]**

For reference on the attentive details of how to configure sudo, see the referenced link above.

Regards
Iain

[EDIT] I should probably put this in a HowTo ;)

---

### Post by drs305 on 2009-04-12
> **tinivole said:**
> [EDIT] I should probably put this in a HowTo ;)

Definitely!

---

