---
title: "URGENT!  ls question"
date: 2009-05-21
forum: General Help
---

### Post by LookUpSeeBlu on 2009-05-21
Hello,

I have a Ubuntu server that is running a specific open source application that is no longer supported.  Unfortunately, I do not have any choice but to continue using this.  There was a change to our proxy server (moved to a new subnet) and I need to change it on this server.  We did this with the export http_proxy command but it is still not working.  I have exhausted all possibilities and now would like to search the file system to see if any files contain the old IP address of the proxy.

# ls -R | while read line; do cat $line | grep OLD_IP ; done

However, the output from -R is causing issues, I am guessing because of the structure.  Is there a way to just have ls do a return a list of files on the file system so I can pass this in?

Thanks for all your help...

Kevin

---

### Post by geirha on 2009-05-21
grep can search recursively. Try with
```
grep -r -I 'old_ip' /path/to/search/
```

The -I option tells grep to ignore searching files that appear to be binary.

Read the man-page of grep for more information
```
man grep
```

---

### Post by LookUpSeeBlu on 2009-05-21
Thanks for the reply!  I would like to use sed to replace the characters.  Something like:

# ls -R | while read line; do cat $line | sed -e 's#OLD_IP#NEW_IP#g' ; done;

Thanks for your response.

---

### Post by geirha on 2009-05-21
Well, if you found some hits with that grep command, you can change it slightly to output a zero-delimited list of filenames, then pipe those files to sed via xargs.
```
grep -rIlZ 'old_ip' /path/to/search/ | xargs -0 -- sed -i~ 's#old_ip#new_ip#g'
```

Note that sed will make a backup with a ~ suffix of each file it changes.

EDIT: Sorry, -rIlz should be -rIlZ (capital Z). Changed it now.

---

