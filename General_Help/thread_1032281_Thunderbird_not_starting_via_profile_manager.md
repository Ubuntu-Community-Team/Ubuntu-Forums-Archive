---
title: "Thunderbird not starting via profile manager"
date: 2009-01-06
forum: General Help
---

### Post by Berduchwal on 2009-01-06
Hi

This used to come up when I tried to run Thunderbird via profile manager:

> The program 'thunderbird-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
(Details: serial 5310 error_code 3 request_code 20 minor_code 0)
(Note to programmers: normally, X errors are reported asynchronously;
that is, you will receive the error a while after causing it.
To debug your program, run it with the --sync command line
option to change this behavior. You can then get a meaningful
backtrace from your debugger if you break on the gdk_x_error() function.) 

Already discussed:
[http://ubuntuforums.org/showthread.php?t=593451](http://ubuntuforums.org/showthread.php?t=593451)
[http://ubuntuforums.org/showthread.php?t=629140](http://ubuntuforums.org/showthread.php?t=629140) 

As the solution above did not work for me but I managed to find work around as follows:

**Step 1**
Make note of the all profile names that you have created. Mine was:
Marcin
Kasia

**Step 2**
Right click on the top panel between clock and System and select “Add to panel” then select “Own program activator” in my version this is the first option on the list.
Put as follows:
Type – Program
Name- Thunderbird Marcin 
Command- thunderbird -p Marcin
Comments – Marcin – Thunderbird
Click OK

**Step 3**
By now your should have thunderbird activator for Marcin profile next move is to create one for the other profiles.
To make icons different I would suggest to take thunderbird icon and turn it red using Gimp so you can easily distinguish which is which. Once this is completed repeat step 2 but before you click OK do the following:
click on the thunderbird icon and select your modified icon
then click OK

In the **Step 2** you need to replace word with “Marcin” with your chosen profile name.

Hope this will help someone!

---

