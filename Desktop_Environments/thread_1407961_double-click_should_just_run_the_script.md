---
title: "double-click should just run the script"
date: 2010-02-15
forum: Desktop Environments
---

### Post by boondocks on 2010-02-15
I have a shell script.  I set the permissions:
chmod 755 ./run_it

So now it is.
-rwxr-xr-x

I open Nautilus File Browser.
Go to the folder that contains "run_it"

I double-click on "run_it" because I want it to run.

Instead of running this shell script, I get the message:
[COLOR="Blue"]Do you want to run "run_it", or display its contents?[/COLOR]
With the buttons...
[COLOR="Blue"]<Run in Terminal>  <Display>  <Cancel> <Run>[/COLOR]

So I click on the [COLOR="Blue"]<Run>[/COLOR] button to run it.

Is there any way to make the script just run by default
and not display this message at all?

---

### Post by chewearn on 2010-02-16
For a workaround, right-click on the desktop, select "Create Launcher", point it to the script.  Now, double-click on the launcher will run the script immediately without asking.

---

### Post by mcduck on 2010-02-16
> **boondocks said:**
> I have a shell script.  I set the permissions:
chmod 755 ./run_it

So now it is.
-rwxr-xr-x

I open Nautilus File Browser.
Go to the folder that contains "run_it"

I double-click on "run_it" because I want it to run.

Instead of running this shell script, I get the message:
[COLOR="Blue"]Do you want to run "run_it", or display its contents?[/COLOR]
With the buttons...
[COLOR="Blue"]<Run in Terminal>  <Display>  <Cancel> <Run>[/COLOR]

So I click on the [COLOR="Blue"]<Run>[/COLOR] button to run it.

Is there any way to make the script just run by default
and not display this message at all?
By default, Nautilus is set to ask what you want to do when you click on a text file that's also set to be executable.

You can set the behavior you want in the file manager's preferences. (the options are to always view the file, always execute the file, or ask what to do).

---

