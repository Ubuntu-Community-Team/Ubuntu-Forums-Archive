---
title: "Problems Changing File/Directory Permissions"
date: 2004-11-27
forum: Desktop Environments
---

### Post by dare2dreamer on 2004-11-27
I found the howto below on a Mandrake linux forum. Does anyone know why this does not work under Ubuntu? When I tried the first command:

```
find ./ -type d -exec chmod u+rwx {} ;
```

I got this error:

```
find: missing argument to `-exec'
```

As a lot of people are switchers, I'm sure I'm not the only one out there who could take advantage of being able to sort out their migrated files and folders.

If someone could help me figure out why this isn't working, I'd be happy to rewrite the following and post it as a "switcher howto". 

> There is a problem that happens frequently when

    * Moving folders from a windows partition,
    * Restoring folders from a CD or DVD. 

All your permissions are lost. In other words, all files and documents are readable, executable, and writable by everyone... This can be a problem, for security reasons, but also for color-coding files in an xterm for instance.

What I usually want personnaly is to restore things so

    * directory are readable, writable, and executable for the owner (and the owner only)
    * files are readable and writable by the owner only, and not executable by anyone. 

Well, it just takes a few commands:

      # find all directories (recursively), and give the owner the permission
      # to read, write and execute
      find ./ -type d -exec chmod u+rwx {} ;
      # find all directories (recursively), and remove all right to
      # group members and the rest of the world
      find ./ -type d -exec chmod og-rwx {} ;
      # find all files (recursively), and give the owner the permission
      # to read, write but not execute
      find ./ -type f -exec chmod u+wr-x {} ;
      # find all files (recursively), and remove all right to
      # group members and the rest of the world
      find ./ -type f -exec chmod og-rwx {} ;

That's all.

---

### Post by dare2dreamer on 2004-11-28
Ok, so after a bit of digging, I found my own solution. :-P

It was an issue of escaping things properly. For example, In the line:

```
 find ./ -type d -exec chmod u+rwx {} ;
```

It should be changed to:

```
 find ./ -type d -exec chmod u+rwx \{\} \;
```

And then this handy trick will work just fine.

---

