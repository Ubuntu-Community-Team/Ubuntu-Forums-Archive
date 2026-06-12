---
title: "Trouble Installing Mupen64 (gtk problems)"
date: 2005-11-14
forum: Gaming &amp; Leisure
---

### Post by *Samuel* on 2005-11-14
Hello Everyone, 
   I've been trying to install Mupen64 0.5 from source, but it seems to be having problems finding the path to my GTK package. Here is the terminal output after I ./configure.

```
Found a working C compiler (gcc).
Checking SDL...
Found SDL version 1.2.8.
Checking GTK 1.2...
*** Couldn't find gtk-config.
Checking GTK 2...
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
./config.temp: line 3: syntax error near unexpected token `('
./config.temp: line 3: `int main(int argc, char *argv[]) { if (gtk_init_check(&argc,&argv) == FALSE) { printf( "gtk_init_check() failed"); return 1; } return 0; }'
*** Couldn't find a working GTK library!
```

It seems like its trying to tell me what to do, but I have no idea where the PKG_CONFIG_PATH variable is (or what it is, for that matter).

Any help would be greatly appreciated. Thanks.

---

