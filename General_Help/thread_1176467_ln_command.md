---
title: "ln command"
date: 2009-06-02
forum: General Help
---

### Post by firsttimeuser on 2009-06-02
i am trying to link the test dir to /tmp/test, and got the following error, could anyone tell me what is wrong with my command? thanks

root@noname:/home# ln -s test /tmp/test
root@noname:/home# cd /tmp/test
bash: cd: /tmp/test: Too many levels of symbolic links

---

### Post by quixote on 2009-06-02
A leading "/" means you're starting at the root of the whole filesystem, to very topmost level.  So as root, which seems to be how you're doing this, you are in the /home directory.  (Users accounts would normally go under this: eg /home/jane, /home/clara etc.)  Root's own home dir is /root.

So your first command is telling it to make the symbolic link "test" inside /home, because that's where you issued the command, and without a full path before the symbolic link, it implies the link is to be made in the current dir.  That's told to link to the directory /tmp/test in the overall filesystem (ie topmost level / tmp / test)

Do you actually have a directory under /tmp called "test"?  If not, then you're asking it to go one level further down than is possible.  If there's no "test" under "tmp" you're asking it to go one level too far down, hence the error message.

Just a question: any reason why you need to do this as actual root, instead of using the (safer) sudo?

---

