---
title: "CVS Cedega Won't start"
date: 2005-12-21
forum: Gaming &amp; Leisure
---

### Post by Evil Whisper on 2005-12-21
hello everyone!

I've downloaded the CVS Cedega install script from linux-gamers.net I've ran it using the user_install profile and everything is well It compiled and installed.

Next i did this:
```

cd ~/.WineCVS/installs/cvscedega/bin

```

Then I did this:
```

./wine

```

Then I got an error about the *.so missing so i did this:

```

cd ..

```

```

cd lib

```

```

sudo cp * /usr/lib/

```

Now all the errors are gone but when I try to run it using ./wine like above it gives me an error saying: "~/.transgaming/drive_c/" not found

next I create that directory and the drive_c directory then i get this error:
"C:/windows" invalid directory.

Can anyone help me out please.

Thanks in advanced
- Evil Whisper

---

