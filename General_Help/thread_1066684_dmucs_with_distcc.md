---
title: "dmucs with distcc"
date: 2009-02-11
forum: General Help
---

### Post by peter c. on 2009-02-11
Hi, I was wondering if anyone has tried running the dmucs tool with distcc. I've been trying following the intructions for installing dmucs given at < [http://dmucs.sourceforge.net/](http://dmucs.sourceforge.net/) >, but its been throwing up errors, and I can't find any useful troubleshooting documentation on the web.

The error I get is as follows: when I run the command < make CPPFLAGS=-DSERVER_MACH_NAME=\\\”titanium\\\” > (titanium being my machine name), it starts compiling, but after a while comes up with:

gethost.cc:84: error: stray ‘\342’ in program
gethost.cc:84: error: stray ‘\200’ in program
gethost.cc:84: error: stray ‘\235’ in program
gethost.cc:84: error: stray ‘\342’ in program
gethost.cc:84: error: stray ‘\200’ in program
gethost.cc:84: error: stray ‘\235’ in program
gethost.cc: In function ‘int main(int, char**)’:
gethost.cc:84: error: ‘titanium’ was not declared in this scope
gethost.cc:87: warning: deprecated conversion from string constant to ‘char*’
make[2]: *** [gethost.o] Erreur 1


The relevant lines in gethost.cc are:
...
 83     std::ostringstream serverName;
 84     serverName << "@" << SERVER_MACH_NAME;
 85     int serverPortNum = SERVER_PORT_NUM;
 86     struct hostent *he;
 87     char *distingProp = "";
...

I hope I haven't missed something ridiculously obvious (I have been known to in the past!). If anyone can offer any help at all, it would be much appreciated!

---

