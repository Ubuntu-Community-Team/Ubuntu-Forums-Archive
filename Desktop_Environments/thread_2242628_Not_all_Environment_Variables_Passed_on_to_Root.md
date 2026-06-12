---
title: "Not all Environment Variables Passed on to Root"
date: 2014-09-03
forum: Desktop Environments
---

### Post by actionmystique on 2014-09-03
Ubuntu Desktop 14.04 LTS

Hello guys,

[LIST]
[*]Some environment variables are defined inside **/etc/environment**, namely PATH, JAVA_HOME and EDITOR. 
[*]The "env_reset" option has been disabled inside **/etc/sudoers**. 
[/LIST]

Yet, the last two variables do NOT appear in root's environment, but the PATH is correctly changed.

Is this a glitch or am I missing something?

---

