---
title: "Adding a path accessible by all programs"
date: 2009-05-20
forum: General Help
---

### Post by XCan on 2009-05-20
When browsing the forums and the internet I've found several places to add a path. What I'm after is a place to add a path, such that it will be accessible for other programs that I open up. In this case, the program in question is Matlab which I want to use to call on programs on my system using the system() command in Matlab.

Anyone have any idea where this should be added?

---

### Post by mbeach on 2009-05-20
I think you may want to edit the 
/etc/environment
file to include the path to your Matlab installation. This file affects all users.

edit: sorry misread - thought you were trying to call Matlab from other programs. I'll take a look into it.

after reading
[http://www.mathworks.com/access/helpdesk/help/techdoc/index.html?/access/helpdesk/help/techdoc/ref/system.html&http://www.google.ca/search?q=matlab+system()&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.mathworks.com/access/helpdesk/help/techdoc/index.html?/access/helpdesk/help/techdoc/ref/system.html&http://www.google.ca/search?q=matlab+system()&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

can you call something like
[status, result] = system('/path/to/my/script/myscript')
if you want to omit the /path/to/my/script in the system call,
can you add a path like /home/myuser/matlabscripts/ to /etc/environment
create a script the echo's 'hello world' named hworld and put it in that folder. Be sure to make it executable (chmod u+x hworld) then try to call it with
[status, result] = system('hworld')

---

### Post by XCan on 2009-05-20
Yah I can, however, it doesn't seems to work properly as the variable I need to append to is $LD_LIBRARY_PATH, which matlab already has defined. Anyhow, I found out that I could simply add an export line in the startup script /usr/local/matlab/bin/matlab. :)

---

