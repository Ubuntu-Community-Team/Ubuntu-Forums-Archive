---
title: "Problems getting crontab to execute script as user(non root)"
date: 2013-08-27
forum: Desktop Environments
---

### Post by Beau_Hodges on 2013-08-27
Hello,
I have a script, report.sh that I am trying to get crontab to run as the local user. It opens sqsh and runs a sql command:

```
#!/bin/bash
sqsh -C 'select * from table'
```

if I run
```
./report
```
it works fine, but as sudo it does not, this is because there are no config files for root.

I've tried adding adding the task system wide, specifying user via
```
/etc/crontab
```
and using both ```
crontab -u user -e
``` and ```
chrontab -e
```

but each time, the job runs, yet fails since it can't find the configuration files/set paths for sqsh.
Any help is appreciated.

---

### Post by 1/0 on 2013-08-27
So, if I understand you correct, cron runs the script at the time you have set but it can't find the sqsh config files. I'm not using sql but it sounds as if you need to set the environment properly. Something like SQSH="/usr/bin/sqsh".

---

### Post by TheFu on 2013-08-27
cron tasks do not have much environment, so you must setup the script to provide any environment variables you need. The PATH, LIBPATH, are usually the big ones, but a cron task does not have a HOME, JAVA_HOME or any DB environment variables set either.

To figure out what might be the cause, run "env" under the userid for the crontab. Look through the output for things that are important to the script.

I agree with 1/0 - set the full path for any external commands that you call and DO NOT assume any current directory. Specify exactly where you want the outputs with a full path.

I should ahve asked first - are you seeing any output from the cron? On some systems, cron is not allowed for all users.  **man crontab** will explain.

BTW, you always want to use **crontab -e** to edit crontabs for any user, including root. It checks the syntax of the schedule file (not the script).

---

### Post by Beau_Hodges on 2013-08-27
> **1/0 said:**
> So, if I understand you correct, cron runs the script at the time you have set but it can't find the sqsh config files. I'm not using sql but it sounds as if you need to set the environment properly. Something like SQSH="/usr/bin/sqsh".

Wow, thank you. How easily I overlooked that. I was trying to add a variable for [COLOR=#B03060]SYBASE=[/COLOR][COLOR=#CCCCCC]~/.sybase [/COLOR]to many different files, but for whatever reason, they would not stick. Adding:

```
export [COLOR=#B03060]SYBASE=[/COLOR][COLOR=#CCCCCC]~/.sybase[/COLOR]
```

to the top of the script corrected the config issues and allowed the script to run. Unfortunately, the files it generates(text files) are owned by root. :/
Thank you again for your help

---

### Post by Beau_Hodges on 2013-08-27
TheFu
Great, thank you for the explanation. "[COLOR=#000000]are you seeing any output from the cron?[/COLOR]" do you mean crontab -l? It does list the cron job, as long as it was set as user via crontab -e(as you suggested). The problem now is getting the files generated from the script to be owned by the user and not root(the sql command above the redirects into a text file by > report.txt).

---

### Post by TheFu on 2013-08-27
> **Beau_Hodges said:**
> TheFu
Great, thank you for the explanation. "[COLOR=#000000]are you seeing any output from the cron?[/COLOR]" do you mean crontab -l? It does list the cron job, as long as it was set as user via crontab -e(as you suggested). The problem now is getting the files generated from the script to be owned by the user and not root(the sql command above the redirects into a text file by > report.txt).

~/whatever is a bad assumption - there is usually not a HOME directory set. Always use the full path to input and output files inside scripts run from cron.

By default, cron emails the output to the useid of the owner of the crontab job. If you haven't setup email to forward somewhere useful, it is on the box (most likely). Use a text CLI mail client to read it.  "Mail" is a good, simlpe, one. Be certain to delete these emails or they can fill up a filesystem and crash a server.  Once you get the crontabs working how you like, you can redirect all output (stderr, stdout) to /dev/null and never see it again.

Once again - **always use full paths for all files in a script run under cron.**

---

### Post by Beau_Hodges on 2013-08-27
> **TheFu said:**
> **always use full paths for all files in a script run under cron.**

Noted, and very much appreciated.

> **TheFu said:**
> Be certain to delete these emails or they can fill up a filesystem and crash a server. Once you get the crontabs working how you like, you can redirect all output (stderr, stdout) to /dev/null and never see it again.

Also great advice. Thank you for all of your help.

---

