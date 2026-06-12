---
title: "program installation - again..."
date: 2006-01-02
forum: General Help
---

### Post by Alex99 on 2006-01-02
looked at all the documentation and I have already installed lots of programs, but this one doesn't work. It's called cisco vpnclient and it's a client that would allow me to use the ethernet in a library. I unpacked the ...tar.gz-file, but the commands configure, checkinstall and make don't work. There's no readme file, and for linux, there's no howto on the cisco website. However, there are files such as "vpnclient," "vpn_install," and "vpnclient_init". If I enter these names, I get the answer "command not found"
Alex

---

### Post by pkaeding on 2006-01-02
[QUOTE=Alex99]However, there are files such as "vpnclient," "vpn_install," and "vpnclient_init". If I enter these names, I get the answer "command not found"
Alex[/QUOTE]

I don't know specifically about that software, but if you are trying to run programs in the current folder (and that folder isn't in your path), you need to run, for instance,

```
./vpnclient
```

This is telling the shell to run the program called vpnclient in the current folder (which is referred to by the dot).

Also, be sure the mode of the file is set to executable.  if you run 

```
ls -l
```

in the folder with the extracted files, you will see the mode of all the files displayed.  you want to be sure it is at least executable for the owner (assuming you are the owner)

---

