---
title: "crontab daily who"
date: 2006-09-26
forum: Desktop Environments
---

### Post by teumima on 2006-09-26
I just setup this Ubuntu box, and I want it to record everyday Sunday through Friday who is using the PC at 15:00.

So I did the following

* 15 * * 0-5 /usr/bin/who > $HOME/who

What is wrong with this?

:-k

---

### Post by Gotterdammerung on 2006-09-26
try changing from **>** to **>>** to append data. and from **$HOME/who** to the complete path where you want the information to be stored. lets say **/home/teumina/who**.

---

### Post by darrenm on 2006-09-26
Crontab doesnt know what $HOME is. 

Better would be:

```
* 15 * * 0-5 /usr/bin/who > ~someone/who
```

depending on what you want to acheive. :)

edit: (being a fool)

---

### Post by teumima on 2006-09-26
So this would work:

40 15 * * 0-5 /usr/lib/who >> ~/bob/who


????

---

### Post by teumima on 2006-09-26
ok guys

thanks it works now.

Great!

so the issue was the $HOME???

---

### Post by nikhilk on 2006-09-26
That is correct. A cron job does not inherit your environment, hence any of your environment variables.

---

### Post by teumima on 2006-09-26
I don't get why this happens.

40 15 * * 0-5 /usr/lib/who >> ~/bob/who

creates the following file in bob's home dir

~bobwho

so if i change the crontab to 


 40 15 * * 0-5 /usr/lib/who >> ~who

I get

~who in bob's home dir

and if i change it to 

 40 15 * * 0-5 /usr/lib/who >> who

i get the file

who in bob's home dir


How does it decide which home dir to use?

---

### Post by darrenm on 2006-09-26
~/bob/who creates a file called ~bobwho in the home directory of the users crontab you are editing. in this case you must be editing cron logged in as bob. Each user has their own crontab.

same for ~who - it will create it in bob. Crontab doesnt read Bash's profiles so only knows the users home dir from /etc/passwd.

same again with who - just creates a file called who for whoever's crontab is running.

~bob/who should work. (not ~/bob/who)

---

### Post by darrenm on 2006-09-26
Also wouldnt it be better to just mail yourself the auth.log file every day?

---

### Post by reclusivemonkey on 2006-09-26
> **darrenm said:**
> Also wouldnt it be better to just mail yourself the auth.log file every day?

~ = /home/username

So if you have /home/bob you don't need ~/bob, just ~

---

### Post by teumima on 2006-09-27
Since this is a function performed by the syem admin. It should ideally be done by root crontab right?

so 

sudo crontab - e 

then 

* 15 * * 0-5 /usr/lib/who ~who

where would this be created? 

And if I wanted it created in bob's account, but bone by the root crontab, what argument would I need then?

* 15 * * 0-5 /usr/lib/who ~bob/who ?
[I]
darrenm:[/I] "Also wouldnt it be better to just mail yourself the auth.log file every day?"

How would I go about doing that?

---

### Post by Gotterdammerung on 2006-09-27
> **teumima said:**
> I don't get why this happens.

40 15 * * 0-5 /usr/lib/who >> ~/bob/who

creates the following file in bob's home dir

~bobwho

so if i change the crontab to 


 40 15 * * 0-5 /usr/lib/who >> ~who

I get

~who in bob's home dir

and if i change it to 

 40 15 * * 0-5 /usr/lib/who >> who

i get the file

who in bob's home dir


How does it decide which home dir to use?

As already told, when you execute crontab under a user session, it inherits some env vars. And it may happen somewhere else. Within a script, for example. That's why I recommended you to use the full path. This way you prevent from changing your system in a unwanted way. :)

---

### Post by darrenm on 2006-09-27
sudo crontab -e will still use the original users crontab. You have to run as root to edit roots crontab.

I would:

```
sudo passwd root
```
```
su -
```
Then put the root password in to log in as root. Run crontab -e and add:
```
0 16 * * 0-5 cat /var/log/auth.log | mail -s "auth.log" bob@somedomain.com
```

This will mail the auth.log to the mail address [email]bob@somedomain.com[/email]

---

### Post by teumima on 2006-09-27
cool thanx.

---

