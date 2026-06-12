---
title: "I need a plugin do Pidgin to send a message to every online contact."
date: 2008-04-03
forum: Desktop Environments
---

### Post by crixtiano on 2008-04-03
Please, 

I need to find a plugin to send a message to every online contact on my  buddy list. 

How to do this using Pidgin?

Thank you.

Cristiano

---

### Post by kevdog on 2008-04-03
The purple plugin pack has a specific plugin called Group Message:

[http://plugins.guifications.org/trac/wiki/PluginPack](http://plugins.guifications.org/trac/wiki/PluginPack)

Notice however this plugin if you follow the general build instructions in disabled by default due to its abuse potential.  

To enable it, here are the specific instructions from the web site:
```
How do I enable a plugin you have not enabled by default? ¶

There are a few ways if you're NOT on Windows. We will cover Windows in a separate question, as it is a different process. You can touch plugindir/.build from the top level source directory and then run the configure script again; this is the easiest way. The second way is to do a for loop in your shell, similar to this for bash: for i in *; do cd $i && make && su -c 'make install' && cd ..; done. The third way is to run the configure script with the argument --with-plugins=plugin1,plugin2,...,pluginN where you specify a comma delimited list of the plugins you want to build. After running the configure script in either way mentioned here, build and install as normal. 
```

Note specifically you need to compile the plugin pack and hence will need the build-essential and linux-header files installed.

---

