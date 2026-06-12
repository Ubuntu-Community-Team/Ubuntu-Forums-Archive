---
title: "Running Scripts"
date: 2005-11-22
forum: Desktop Environments
---

### Post by Toolsmith on 2005-11-22
In Windows, once I have created hello.perl containing the single line
     print "hello, world\n";
I can invoke it by typing in "hello".  In order to do that I have to add .perl to the pathext envvar and sett up associations using assoc and ftype so that cmd will know what to run.

In ubuntu I added the first line
     #!/user/bin/perl
and then figured I could probably enter "hello.perl" but bash says "hello.perl: command not found".  What am I missing?

Thanks -

---

### Post by simplyw00x on 2005-11-22
You need to remember that Bash tries to execute a script from a directory in the $PATH variable when you just type a name.

To get it working, add ./ (dot slash) at the start, hence:
```
./hello.perl
```

---

### Post by Toolsmith on 2005-11-22
"Permission Denied."

I assume I need to learn more about permissions in *ux.

But once I've done that, is there a way in bash to get to the simplicity of execution "hello" I've gotten used to in Windows?

---

### Post by dmh-bidlah on 2005-11-22
You need to make hello.perl executable.
Do that with
```

$ chmod +x hello.perl

```
Or set the permissions in Nautilus,

---

### Post by Toolsmith on 2005-11-22
Thanks.  I just found that.  Works a charm.

2 questions:

1) would it be a Mistake to add ./ to the path?

2) Can I tell bash to not require the extension?

---

### Post by rgrig on 2005-11-22
1. generally yes; you'll get windows' broken behaviour if you do :p

2. just don't use extensions if you don't like them; but, remember, if typiing too much is your problem then TAB is your friend.

---

