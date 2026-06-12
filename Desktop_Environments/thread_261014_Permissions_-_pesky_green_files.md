---
title: "Permissions - pesky green files?"
date: 2006-09-19
forum: Desktop Environments
---

### Post by Anything Generic on 2006-09-19
Tomcat is having some issues compliling .jsp code.  Any files that are colored Green when I do an 'ls' do not work correctly.  Files that are colored White work without a hitch.

*How do I get the green files white?*  I really wish there was a more intelligent way to put that. ABC-123.  I mucked around with chmod 755 but that didn't help.  Any suggestions?

Thanks
-Eric

---

### Post by jtwJGuevara on 2006-09-19
What is the user that tomcat runs under?  

Paste the output of the following command:

```
ls -l
```

Those two bits of information should help.

Also, files that are green indicate files that are executable.  Files that are white are just plain files and nothing special can be done to them other than reading/writing.

---

### Post by Anything Generic on 2006-09-19
There was a tomcat user created.  I don't know if tomcat runs under this.  I would assume so?

As for ls -l, what folder would you like me to do this for?

Thanks for the help!

---

### Post by skymt on 2006-09-19
Green files have execute permissions. Run "chmod a-x *.jsp", or just do it in Nautilus.

---

### Post by jtwJGuevara on 2006-09-19
Perform ls -l in the directory where your .jsp files are located.  Also perform ls -l on the parent directory.  

I'm guessing that Tomcat can't compile the .jsp files if it doesn't have read permission on them or possibly the parent directory.

---

