---
title: "[SOLVED] shutdown from awesome"
date: 2008-11-12
forum: Desktop Environments
---

### Post by ad_267 on 2008-11-12
In openbox I added this command to my menu so that I could shut down my computer: "gdm-control --shutdown && openbox --exit"

I want to add something like this to the menu in Awesome, but I there doesn't seem to be a command to quit Awesome, only a function in the lua configuration file. I can't figure out how to execute a command and then the function from the menu. My menu looks like this at the moment:

```
myawesomemenu = {
   { "manual", terminal .. " -e man awesome" },
   { "edit config", editor_cmd .. " " .. awful.util.getdir("config") .. "/rc.lua" },
   { "restart", awesome.restart },
   { "quit", awesome.quit }

```

I tried adding:
```
{ "shutdown", "gdm-control --shutdown && " .. awesome.quit }
```
But awesome.quit is a function, not a string so this doesn't work. Anyone have any ideas?

Also, any idea why Awesome sometimes randomly quits when I exit from a terminal, or any other program. How would I find out what's going on?

I'm using Awesome 3 from git, and followed this guide: [http://awesome.naquadah.org/wiki/index.php?title=Awesome-3-git-Ubuntu-Intrepid](http://awesome.naquadah.org/wiki/index.php?title=Awesome-3-git-Ubuntu-Intrepid). Maybe I should be using a more stable version?

Edit: Solved, for anyone who's interested I just had to do:
```
{ "Shutdown", function () awesome.spawn("gdm-control --shutdown"); awesome.quit() end}
```

And the randomly quitting was a bug that has now been fixed.

---

