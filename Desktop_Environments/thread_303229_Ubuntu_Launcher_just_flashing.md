---
title: "Ubuntu Launcher just flashing"
date: 2006-11-19
forum: Desktop Environments
---

### Post by troach on 2006-11-19
When I execute an executable from the terminal via bash, it opens. When I try and do it in the launcher, I select Application in Terminal, put the same executable, and it just flashes. I set this up in gnome on Fedora with the same executable and it works fine. Any ideas if this is a bug?

I created a Launcher for vi the same way and it opened. I am so stumped.

I know the executable work because I go to the Terminal and type in sqlplus an it just works. With the launcher it flashes and nothing.

---

### Post by troach on 2006-11-19
Problem kind of solved. I had to set the environment variable ORACLE_HOME. The ORACLE_HOME is set in my .bash_profile. Should I put it in another file so it will be a global environment variable? .bashrc? Any ideas? Thanks

---

