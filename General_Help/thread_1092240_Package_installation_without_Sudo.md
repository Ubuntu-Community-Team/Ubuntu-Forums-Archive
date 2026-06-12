---
title: "Package installation without Sudo"
date: 2009-03-10
forum: General Help
---

### Post by newbe5 on 2009-03-10
I originally posted this i the wrong section, so this is pasta :D

Forgive me if this has been gone over a thousand times, but I'm going to ask anyway :P

Is there a way fro me to set up a "Trusted APT repository" from which users can install software without the need to enter a sudo password? This is so I can distribute software in an enterprise-like environment without giving users access to install software from ordinary repositories.

Also, while I'm on the subject, can anyone reccomend good tools for use with Ubuntu in an enterprise managed environment? This isn't for production machine currently, I'm just testing the software out to see what it might be capable of.

Thanks in advance!

newbe5

---

### Post by Aries-Belgium on 2009-03-10
Although it's a bad idea you could setup sudo to not require a password. Look at [this howto](http://blog.crowdway.com/2008/01/27/passwordless-sudo/). As you can see you can specify which commands don't need a password from the users.

---

### Post by 3Miro on 2009-03-10
On one side I understand the passwrd requirement and on another I don't. I can download the source for any program compile and run it without the need for sudo.

I wish repositories allow installing packages for the local user only without the need for a password (or maybe just the regular user's pass).

---

### Post by newbe5 on 2009-03-10
So this isn't natively possible without some fiddling? All I really needed was a repository that has a lit of approved packages (ones that I have approved) that the users can install if they want without the need to call me for a password. But I DONT want them to be able to install packages from other sources.

It would also be nice if I could use this method to approve ubuntu updates so they can also be installed without a password.

---

### Post by halovivek on 2009-03-10
If it happens like that then it will be security breach and some one can take control of the system. example like windows which gets virus and spyware.

---

### Post by snowpine on 2009-03-10
sudo should always be required when making changes outside the user's home folder, in my opinion. It is common sense security.

---

### Post by SeanHodges on 2009-03-10
> **3Miro said:**
> On one side I understand the passwrd requirement and on another I don't. I can download the source for any program compile and run it without the need for sudo.

You would need sudo to give your compiled program permission to modify system files and listen on IANA-registered ports... The package manager can do this for you, but you still need to provide a password.

> I wish repositories allow installing packages for the local user only without the need for a password (or maybe just the regular user's pass).

So what happens when you run a script that secretly runs apt-get to retrieve a tool that can be exploited? The password request is mainly a way of saying "Another program wants to install a package, are you happy with this?" as well as "You *are* permitted to do this, yes?"

> **newbe5 said:**
> So this isn't natively possible without some fiddling?

That is correct, you will need to modify your system to disable this security. What you are asking for is outside the normal use-case that Ubuntu caters for out-of-the-box.

> **newbe5 said:**
> All I really needed was a repository that has a lit of approved packages (ones that I have approved) that the users can install if they want without the need to call me for a password. But I DONT want them to be able to install packages from other sources.

It would also be nice if I could use this method to approve ubuntu updates so they can also be installed without a password.

You can do both of these by modifying the sudo settings. Unfortunately it is forbidden to explain this procedure on these forums for various reasons, but you can find this information easily on the Web.

---

### Post by orethrius on 2009-03-10
> **SeanHodges said:**
> You can do both of these by modifying the sudo settings. Unfortunately it is forbidden to explain this procedure on these forums for various reasons, but you can find this information easily on the Web.

Am I to understand that setting up rsync mirrors that can take care of the "local packages I approve" part is also verboten?

---

### Post by upchucky on 2009-03-10
what you are trying to do is a very silly thing, the whole point of a secure os is not being able to bypass security.

the reason windows and software written for windows is the best virus catcher and exploitable os, is because it already does what you are trying to do by reason of its poor design.

I suggest you rethink the security aspect of what you really want.

---

### Post by oldos2er on 2009-03-10
"I wish repositories allow installing packages for the local user only without the need for a password (or maybe just the regular user's pass)."

 It isn't the repository that requires a password, it's your system.

---

### Post by newbe5 on 2009-03-11
> **upchucky said:**
> what you are trying to do is a very silly thing, the whole point of a secure os is not being able to bypass security.

the reason windows and software written for windows is the best virus catcher and exploitable os, is because it already does what you are trying to do by reason of its poor design.

I suggest you rethink the security aspect of what you really want.

What I want is to be able to distribute software to client machines with little or no user input or intervention. If there is another way of doing this then fine, but saying that an OS is "Too secure to have helpful features." is a pile of BS I'm afraid. There is nothing un-secure about Windows client systems if you secure them properly.

Please, if you dont have a contructive answer then don't post.

---

### Post by amac777 on 2009-03-11
> **newbe5 said:**
> What I want is to be able to distribute software to client machines with little or no user input or intervention. If there is another way of doing this then fine

Disclaimer: I am not an expert in this (although I am interested in learning how to use Ubuntu in an enterprise environment for future possibilities).

That said, depending on how many users you need to support etc, you might try something simple like this:

1. Setup a local repository
2. Change the /etc/apt/sources.list files on all the clients to include the local repository (or for added security, to only point to the local repository)
3. Setup a script that runs as root via cron or upon startup on the clients that will update / install software from the local repository. 

To make it flexible, the script that gets run could be located on a networked server so you would only have to update one file and then all the clients would react accordingly the next time they execute the script. Say you want to install newProgram, you just put the newProgram package in the local repository and then add this line to the script:

apt-get install newProgram

The clients would then install it the next time they run the script. Since it all happens behind the scenes (either at boot or via cron), your users would not have to do anything (except maybe turn on the computer in the morning). No sudo passwords required for your users.

---

### Post by newbe5 on 2009-03-11
Good idea! It's not as compartmentalised as I was looking for as a direct clone of something like SMS, but that could still work nicely, thanks for your input!

I'm going to give that a go :)

Anyone else have any ideas?

---

### Post by orethrius on 2009-03-12
It's possible that you could use rsync mirrors, or something with sftp over SSH channels locked to machine-unique fingerprints; in fact, the latter wouldn't be a bad way to maintain the former.  That is to say: the fingerprints could be used to allow establishing an sftp connection to one system that maintains the list of installable packages; then those machines could synchronize with a single system, which would have an rsync line in the Software Sources application on each client system.

---

