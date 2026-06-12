---
title: "about library files' location"
date: 2006-05-28
forum: Desktop Environments
---

### Post by earthvisitor on 2006-05-28
Hi,
I compiled some library which was not available through Ubuntu repositories. When I try to run test applications the shared library cannot be found *IF* I put them in some arbitrary place mentioned *in the PATH variable*. However, if I put them somewhere like /lib, or /usr/local/lib, then it works. 

If I didn't do something stupid inadvertently, this problem seems to exist only for shared library files, as other executables works without problem wherever I put them.

My question: Is there an environment variable or a setting somewhere deep in the system that determines this behavior? If so, is it possible to customize the path for shared libraries? Or, did I just messed things up somehow and illusioned myself :).

Regards and thanks in advance!

N.

---

### Post by tonyr on 2006-05-28
Library directories should be listed in the the environment variable **LD_LIBRARY_PATH**.  Is
that the one you are using?

---

### Post by earthvisitor on 2006-05-28
[QUOTE=tonyr]Library directories should be listed in the the environment variable **LD_LIBRARY_PATH**.  Is
that the one you are using?[/QUOTE]

I don't know what that is... I tried adding the directory to the PATH variable: I renamed the .bash_profile file to .profile, and it contains some extra entry for the PATH variable. So, where can I edit LD_LIBRARY_PATH variable? In what file is it?

---

### Post by tonyr on 2006-05-28
[QUOTE=earthvisitor]I don't know what that is... I tried adding the directory to the PATH variable: I renamed the .bash_profile file to .profile, and it contains some extra entry for the PATH variable. So, where can I edit LD_LIBRARY_PATH variable? In what file is it?[/QUOTE]

It does not exist by default.  You have to create it.  Here is an example I found
at [URL="http://www.nersc.gov/vendor_docs/intel/c_ug/lin1093.htm"]
http://www.nersc.gov/vendor_docs/intel/c_ug/lin1093.htm[/URL]:

> 
    *  command line: prompt>export LD_LIBRARY_PATH=/libs:$LD_LIBRARY_PATH
    * startup file: export LD_LIBRARY_PATH=/libs:$LD_LIBRARY_PATH


Your startup file would be **.bashrc** or **.profile** or **.bash_profile**.
Where the examples say **/libs**, substitute your library path directory
name.  The examples should work whether LD_LIBRARY_PATH already exists
or not.  You could also just say
> 
export LD_LIBRARY_PATH=/libs

in your .profile (or wahtever shell startup file you are using).

---

### Post by earthvisitor on 2006-05-29
[QUOTE=tonyr]It does not exist by default.  You have to create it.  Here is an example I found
at [URL="http://www.nersc.gov/vendor_docs/intel/c_ug/lin1093.htm"]
http://www.nersc.gov/vendor_docs/intel/c_ug/lin1093.htm[/URL]:



Your startup file would be **.bashrc** or **.profile** or **.bash_profile**.
Where the examples say **/libs**, substitute your library path directory
name.  The examples should work whether LD_LIBRARY_PATH already exists
or not.  You could also just say

in your .profile (or wahtever shell startup file you are using).[/QUOTE]

Thank you for your guidance. When I added the export line to my .bashrc the problem is solved. I don't know why, but when I added it to the end of my .profile file, it didn't work. .bash_profile already failed to work for PATH variable. I really don't have slightest idea why this happens, since from what I see, .profile just imports the .bashrc file... Strange.

Thanks again.

N.

---

