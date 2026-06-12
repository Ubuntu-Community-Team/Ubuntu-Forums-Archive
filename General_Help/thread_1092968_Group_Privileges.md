---
title: "Group Privileges"
date: 2009-03-11
forum: General Help
---

### Post by measekite on 2009-03-11
Using a GUI, how to you assign and remove privileges to a group.

How do you add one Group to another using the GUI

---

### Post by MaxIBoy on 2009-03-11
What GUI are you talking about?

On Ubuntu 8.04 with GNOME (that is, not Kubuntu or Xubuntu, just normal Ubuntu,) it's "system>administration>users and groups." If you still use 7.04 like your profile says, I don't know if it works with that version (and 7.04 is no longer supported anyway so you should upgrade.) On 8.10, I don't know if it's the same but I think it is.


Basically, there's no need to have a phoboa of the GUI. The command line is going to be the same across almost all Linux distros, and we don't have to muck around with different instructions for each distro. That's why, nine times out of ten, tutorials just use the command line.

---

### Post by measekite on 2009-03-11
> **MaxIBoy said:**
> What GUI are you talking about?

On Ubuntu 8.04 with GNOME (that is, not Kubuntu or Xubuntu, just normal Ubuntu,) it's "system>administration>users and groups." If you still use 7.04 like your profile says, I don't know if it works with that version (and 7.04 is no longer supported anyway so you should upgrade.) On 8.10, I don't know if it's the same but I think it is.


Basically, there's no need to have a phoboa of the GUI. The command line is going to be the same across almost all Linux distros, and we don't have to muck around with different instructions for each distro. That's why, nine times out of ten, tutorials just use the command line.

I thought I used the Ubuntu prefex to this thread so Gnome would be the GUI.  I know about System>Administration and can already create users and create groups.

But I do not know if or how to:

Add one group to another.  In Windows a group can contain users and other groups.  I do not know about Linux and am having a hard time finding out.

The next question is how do you assign and take away privileges to a group.  In Windows there is a dialog where you can assign various rights to a group or take them away.  I have researched and came up empty on that one also.

---

### Post by MaxIBoy on 2009-03-11
I don't think you can have one group be a member of another group. I think you may have to add them manually.

I do know that the command line for taking everyone in group1 and making them also members of group2 is this:
```
 for i in $( grep group1 /etc/group | cut -d':' -f4 | sed -s "s/,/ /g"); do sudo usermod -G group2 $i; done

```

If that's too annoying to remember, make a function of it in .bashrc (which will be in your home directory.)

So for example, add some lines to the .bashrc file which look like this:
```
 function addGroups {
    for i in $( grep $1 /etc/group | cut -d':' -f4 | sed -s "s/,/ /g")
         do sudo usermod -G $2 $i; 
    done

```

Then, either run "sudo source ~/.bashrc" or restart so that the changes you made to the file will be applied.

If you call the function like this:
```
addGroups group1 group2
```
Then $1 will be replaced with "group1" and $2 will be replaced with "group2." If you called the function like this:
```
addGroups stylishGroup coolGroup
```
Then $1 and $2 will be replaced with stylishGroup and coolGroup, respectively. 



Anyway, I don't think GNOME's gui has features like that, and if it does, then I don't care.

---

