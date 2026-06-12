---
title: "Edit applications menu and PATHs"
date: 2012-10-28
forum: Desktop Environments
---

### Post by El Tito on 2012-10-28
Hi everybody. I'm new to the forums. I have been using ubuntu for a couple of years, but never posted before. I'm interested in understanding how the stuff works. 
I searched in the forums about setting the PATH and making the change permanent, but all I found are a bunch of instructions to get the things done, with little explanation.

Correct me if I state something that is not right.  When you add something to the PATH, via command line you need to export; for example:

PATH=/whatever:$PATH
export PATH

When you do that, the changes take place in the current session, and after you close it, the changes are gone. Maybe the question is too simple, but why do you need to export?, I mean, with the first command above, you succesfully add '/whatever' to PATH, and is possible to run executable files inside '/whatever'.

The second question is, I read a lot of posts in which some people add PATH to the end of the file '.bashrc', others to '.profile'. I'm running kubuntu 12.10, what's the difference?, the first is only for CLI and the second is valid for GUI?. Writing inside these files, do I need to add the mentioned PATH and export, or only PATH is enough?

The last question is about the edit applications option in the KDE menu. I have created a launcher, and if I specify the absolute path to that executable in 'command'(general tab), I get the program running without problems. If i set the working directory in the advanced tab, to '/whatever', I was expecting that only calling the name of the program in 'command' would be enough, to execute it but not working. Also, if I have added to PATH that working directory, why can't I simply call the program by name in 'command'?

Thank you very much in advance, and sorry about my english (non native speaker).
See you around!!

---

### Post by drmrgd on 2012-10-28
In answer to your first question, the 'export' builtin command exports that variable to the environment.  So, the first command alters the variable $PATH, while the second actually exports the variable $PATH to the environment (in this case it's the shell environment) so that the shell can see the newly changed variable.  Here's a nice little guide on the export command:

[http://www.thegeekstuff.com/2010/08/bash-shell-builtin-commands/](http://www.thegeekstuff.com/2010/08/bash-shell-builtin-commands/)

To your second question, your assumption about CLI (the shell environment) vs the GUI environment is correct.  So, if you want the new path to be executed by both the GUI and the shell, you should put that in ~/.profile.  So, for example, there's already built in support for a 'bin' directory inside your $HOME directory (that is, if you create a directory called 'bin' inside of your /home directory, when the shell is reloaded it'll pick this up and add it to your $PATH.  You can see that code inside of ~/.profile:

```
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
```

It's basically saying, if there's a 'bin' directory inside of $HOME, append it to the current path.  Since profile is loaded upon creation of a new session, there's no need to explicitly export the new variable.

I'm not entirely sure about launchers as I don't usually make them.  However, if you've added the path of the binary (or executable script) to your $PATH in ~/.profile and you've made the script or binary executable:

```
chmod +x /whatever/yourscript #NOTE: need 'sudo if /whatever is not owned by root
```

Then I think you should be able to execute it by simply typing the name.  Probably the easiest case would be to create a $HOME/bin directory, add an executable script, reload the session, and try to run the command from anywhere.  Also a quick way to see if it's being picked up correctly would simply be to run:

```
which script
```

Where 'script' is the name of your script in the binary directory you created.  If you created it in $HOME/bin and the result of the above command gives you similar output to:

```
which example.sh 
/home/<username>/bin/example.sh
```

Then you know it's working correctly, and just typing 'example.sh' from anywhere should work.

Hope that helps!

---

### Post by El Tito on 2012-10-28
Thank you very much for your clear and useful explanation drmrgd !

---

