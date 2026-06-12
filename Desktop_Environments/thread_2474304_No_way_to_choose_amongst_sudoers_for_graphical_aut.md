---
title: "No way to choose amongst sudoers for graphical authentification in Gnome"
date: 2022-04-26
forum: Desktop Environments
---

### Post by iutech on 2022-04-26
One of our Ubuntu users is using the default Gnome.
Problem is, when he or his coworkers want to use the GUI for a commande that requires sudo rights (like using the Software Center) there is no  drop-down menu in the authorization windows to offer a list of the the  sudoers accounts, it requires my account's password (as tech support we have an account on all computers).

On Mate or XFCE this drop-down menu is automatic, but I can't find a way to get this drop-down menu in Gnome.

I tried looking up for a solution but none of the keywords I use in DDG seems to work...

---

### Post by QIII on 2022-04-26
Are users logging in to different sessions for their own accounts?

---

### Post by ActionParsnip on 2022-04-26
Could use:
```

su -c gksudo foo

```
Which will run gksudo as foo and you will need to use foo's password to authenticate (you'll also need it for the su authentication).

---

### Post by iutech on 2022-04-26
> **QIII said:**
> Are users logging in to different sessions for their own accounts?

Yes they are.
The main use case is for students using the computer (who do not have sudoer rights) wanting to install something, they're not computer-savy (nor is really their teacher) so they need to use the GUI, and they would need to be able to choose their teacher's account so he can unlock the rights for them (their teacher's desk is next to the computer, while we tech support are much farther away - also we don't necessarily know what he allows his students to install or not).

---

### Post by iutech on 2022-04-26
> **ActionParsnip said:**
> Could use:
```

su -c gksudo foo

```
Which will run gksudo as foo and you will need to use foo's password to authenticate (you'll also need it for the su authentication).

That could be an option but the idea is to not resort to CLI...
Also it surprises me that I can't find an easier way to do that, in MATE or XFCE I have the drop-down menu automatically in GUI.

The users are accustomed to Gnome and don't really want to switch to MATE nor XFCE, alas.

---

### Post by Paddy Landau on 2022-04-26
> **ActionParsnip said:**
> ```
su -c gksudo foo
```
gksudo has been deprecated for some time. It isn't available on Ubuntu 20.04; I haven't tried it on 22.04 yet.

---

### Post by Paddy Landau on 2022-04-26
> **iutech said:**
> … they would need to be able to choose their teacher's account … their teacher's desk is next to the computer…
The easiest way that I can think of is for the teacher to start a new session on the computer with their own account, install the software, and log out, handing control back to the student.

In Ubuntu 20.04, the default GUI session is number 2, and there's another GUI in number 1. You might not know that you can switch between sessions with Ctrl+Alt+F*n*, where *n* is the session number. (Sessions 3 and up are console-only; if the teacher is happy with the command line, that's an alternative.)

Unfortunately you forgot to tell us which version of Ubuntu is being used, so it might be that the default GUI is session 1, and the other GUI in session 2. In that case, swap the numbers in the instructions below.

So…

[LIST]
[*]Press Ctrl+Alt+F1 to start a new login in session number 1. (The student remains safely logged in session number 2.)
[*]The teacher logs into the GUI, installs the software, and logs out (*not* restart or power off).
[*]Press Ctrl+Alt+F2 to return to the student's account in session number 2.
[/LIST]
If you've never tried this before, try it yourself now. Press Ctrl+Alt+F1 to see what happens, then Ctrl+Alt+F2, then Ctrl+Alt+F3, etc.

---

### Post by ActionParsnip on 2022-04-26
> **Paddy Landau said:**
> gksudo has been deprecated for some time. It isn't available on Ubuntu 20.04; I haven't tried it on 22.04 yet.

My mistake. TBH I don't run GUI apps as root. I pretty much live in the terminal apart from Web browsing

---

### Post by Paddy Landau on 2022-04-26
> **ActionParsnip said:**
> I don't run GUI apps as root.
In this case, it's usually the authorisation that's required after starting the GUI app (not always, e.g. Synaptic Package Manager).

I know what the OP means; there used to be a way to select the user. That doesn't seem to be the case any more.

---

### Post by iutech on 2022-04-27
> **Paddy Landau said:**
> In this case, it's usually the authorisation that's required after starting the GUI app (not always, e.g. Synaptic Package Manager).

I know what the OP means; there used to be a way to select the user. That doesn't seem to be the case any more.

Yes, that's it.
It still works in Mate and XFCE, but not in Gnome.

The computer is on Focal Fossa.

I used tty1 to 5 often, I didn't know that Ubuntu changed the way they worked.

It's indeed possible to use ctrl+alt+F1 to change the session, I'll tell the teacher that, but it's still weird to have to go to such extremities rather than just configure the authorization window (if I could find a way to do so)...

---

### Post by Paddy Landau on 2022-04-27
> **iutech said:**
> … it's still weird to have to go to such extremities rather than just configure the authorization window...
You might want to raise a bug report for this.

---

### Post by Paddy Landau on 2022-04-27
I have just tested this on Ubuntu 22.04.

When a standard user asks to install something from the Software Centre, it prompts for the *administrator's* password.

Which version of Ubuntu are you using?

---

### Post by iutech on 2022-04-27
> **Paddy Landau said:**
>  it prompts for the *administrator's* password.


What is the administrator's password ?
I wasn't aware of an administrator account save root (which isn't active on this computer) and the various people with sudo rights ?

This computer is using Focal Fossa and up to date.

---

### Post by Paddy Landau on 2022-04-27
> **iutech said:**
> What is the administrator's password ?
An *administrator* is anyone who has administration rights. That would include the teacher; the teacher is an administrator.

Any other user is a *standard* user.

root is an administrator, obviously, but for safety reasons, it doesn't have a password on a many distributions, including Ubuntu and derivatives (so, no one can log into root directly).
> **iutech said:**
> This computer is using Focal Fossa and up to date.
That's 20.04. I've just tried it on 20.04, and it also prompted for the administrator's password.

I think that I need some more information to figure out why yours is not doing this.

It is possible that the teacher isn't an administrator, and instead has been given specific permission just to install apps. See if the sudoers file contains special instructions for the teacher or for a group that the teacher belongs to. In that case, there probably won't be a prompt, though I haven't tested this.

So…

[LIST]
[*]List the teacher's groups, and check the sudoers file to see if special permissions have been given to the teacher or one of the groups to which the teacher belongs.
[/LIST]
Also…

[LIST]
[*]Are you sure that this is Ubuntu 20.04, and not an official derivative (e.g. Lubuntu, Ubuntu Studio) or an unofficial derivative (e.g. Mint, POP_OS!)?
Open a terminal and run these two commands. Let me know the output of both of them.
```
env | grep -F XDG_CURRENT_DESKTOP
echo $DESKTOP_SESSION
```
[/LIST]

[LIST]
[*]How many administrators and standard users are on the computer (approximately)? I can replicate the setup on my virtual machine to see what happens.
[/LIST]



[LIST]
[*]Are you sure that the student isn't an administrator? Open a terminal, and enter this command, but replace "paddy" with the student's actual username.
```
groups paddy
```
Show me the result. For confidentiality, please obfuscate the student's username.
[/LIST]

---

### Post by iutech on 2022-04-27
> **Paddy Landau said:**
> An *administrator* is anyone who has administration rights. That would include the teacher; the teacher is an administrator.


Thanks.
But then why "administrator" is singular here ? It should ask for any administrator/sudoer password, and offer to choose which (that's what happens in Mate or XFCE).
The tech support account (the one which is shown in the authorization windows) is the first I created, I believe.
Maybe that's why it is considered *the* administrator account rather than *one of the *administrator accounts ?
Still, it's stupid...

> **Paddy Landau said:**
> 
That's 20.04. I've just tried it on 20.04, and it also prompted for the administrator's password.


It does.
What it doesn't is allow to choose amongst the administrator accounts.
And what it considers being *the* administrator is the tech support account, not the teacher's account.



> **Paddy Landau said:**
> 

It is possible that the teacher isn't an administrator, and instead has  been given specific permission just to install apps. See if the sudoers  file contains special instructions for the teacher or for a group that  the teacher belongs to. In that case, there probably won't be a prompt,  though I haven't tested this.

So…

[LIST]
[*]List the teacher's groups, and check the sudoers file  to see if special permissions have been given to the teacher or one of  the groups to which the teacher belongs. 
[/LIST]


I did the installation (I mean, it came pre-installed, but I created the users and everything), and just added the teacher's account to the sudo group with usermod.

Anyway I checked the /etc/sudoers file, and everything is standard (%sudo    ALL=(ALL:ALL) ALL)

There is an admin group in /etc/sudoers; I never used it and the command "members" says it doesn't exist. Anyway neither the tech support account nor the teacher's are members of admin (though both are members of sudo).



> **Paddy Landau said:**
> 

[LIST]
[*]Are you sure that this is Ubuntu 20.04, and not an  official derivative (e.g. Lubuntu, Ubuntu Studio) or an unofficial  derivative (e.g. Mint, POP_OS!)?
Open a terminal and run these two commands. Let me know the output of both of them.
```
env | grep -F XDG_CURRENT_DESKTOP
echo $DESKTOP_SESSION
``` 
[/LIST]


From what I know, yes.
Your command returns an empty line when I use it remotely through an XFCE session in X2Go.
lsb_release -a returns 

```
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.2 LTS (fossa-ditto X84)
Release:    20.04
Codename:    focal
```



> **Paddy Landau said:**
> 
[LIST]
[*]How many administrators and standard users are on  the computer (approximately)? I can replicate the setup on my virtual  machine to see what happens. 
[/LIST]



[LIST]
[*]Are you sure that the student isn't an administrator?  Open a terminal, and enter this command, but replace "paddy" with the  student's actual username. 
[/LIST]


There are AFAIK three sudoers and two students as of now.
groups student returns only the student group (I mean, the group that is specific to that student; I have not created a group for students yet).

---

### Post by Paddy Landau on 2022-04-27
> **iutech said:**
> It should ask for any administrator/sudoer password, and offer to choose which (that's what happens in Mate or XFCE).
I agree.
> **iutech said:**
> The tech support account (the one which is shown in the authorization windows) is the first I created, I believe.
Maybe that's why it is considered *the* administrator account rather than *one of the *administrator accounts ?
No, there's no hierarchy. All administrator users are equal in importance.
> **iutech said:**
> It does.
What it doesn't is allow to choose amongst the administrator accounts.
And what it considers being *the* administrator is the tech support account, not the teacher's account.
Ah. That was unclear in your previous notes.

Anyway…

I've just replicated this on my system.

[LIST]
[*]One administrator (me)
[*]One administrator
[*]One standard user, but added to group *sudo*
[*]One standard user
[/LIST]
I logged into the standard user, and asked to install software. I was prompted only for my password. The other two weren't given as options.

So, yes, it's a genuine problem.

I suggest that you raise a bug report for this, because it's definitely not ideal.

I'm sorry that I don't have a solution for you!

---

### Post by QIII on 2022-04-27
Closed for further review.

---

### Post by QIII on 2022-04-28
After clarification of who will be conducting the authorization, which I misunderstood initially, this thread is reopened.

---

### Post by TheFu on 2022-05-02
Stepping back, couldn't the teachers provide a list of software to install for their classroom machines and IT can remotely install that list using ssh or ansible or whatever devops tool is used there?  Then the ansible playbook would be carried forward from semester to semester and when a package isn't available, the teach can be prompted to remove it from the list.

Pre-solving issues is how we like to work, not reducing overall security.  Though I consider Gnome to be highly detrimental to system security due to all the 'convenience choices they make rather than being secure.  

IMHO. YMMV.

---

