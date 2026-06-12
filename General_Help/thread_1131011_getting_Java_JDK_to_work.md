---
title: "getting Java JDK to work"
date: 2009-04-20
forum: General Help
---

### Post by gremlin12 on 2009-04-20
Hi, I am unable to get my java JDK working. Can anybody help?  I have 2 JDK's installed (the open version and the Sun version 6) but i can't get either one to work. Have tried changing the path, etc., but it still won't work. I'm sure I'm doing something wrong but am totally lost. Thanks.

---

### Post by codeseer on 2009-04-20
See here:

[http://ubuntuforums.org/showthread.php?t=1113039]("http://ubuntuforums.org/showthread.php?t=1113039")

---

### Post by gremlin12 on 2009-04-20
thanks, Codeseer, this Tutorial is great :)

But i'm stuck again...

I got to #4 in the tutorial, and I typed "chmod +x jdk-6u13-linux-x64.bin" in the terminal, and it said:

chmod: cannot access `jdk-6u13-linux-x64.bin': No such file or directory

---

### Post by codeseer on 2009-04-20
> **gremlin12 said:**
> thanks, Codeseer, this Tutorial is great :)

But i'm stuck again...

I got to #4 in the tutorial, and I typed "chmod +x jdk-6u13-linux-x64.bin" in the terminal, and it said:

chmod: cannot access `jdk-6u13-linux-x64.bin': No such file or directory

Well you need to make sure that your terminal path is where the file is; you can do this by typing "pwd" or "ls -al | grep *.bin".
Then you could check the file name. However, you could probably just use "chmod +x jdk*.bin".

---

### Post by jespdj on 2009-04-20
> **gremlin12 said:**
> Hi, I am unable to get my java JDK working. Can anybody help?  I have 2 JDK's installed (the open version and the Sun version 6) but i can't get either one to work. Have tried changing the path, etc., but it still won't work. I'm sure I'm doing something wrong but am totally lost. Thanks.
What does it mean when you say "it doesn't work"? Do you get an error message? If so, then what is the error message?

Note: If you don't have a special reason to install the JDK manually, you can just install the version from the Ubuntu repository:
```
sudo apt-get install sun-java6-jdk
```
See also this: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by gremlin12 on 2009-04-20
The problem isn't installing it, its that it doesn't work when i try to run a java script. it wouldn't be be able to find the file. I tried so many different ways, nothing worked. Some forums say add the path in etc/environment, i tried that, that didn't work either.:(

  im about ready to throw the machine out the window or give up on java entirely

but thanks for the url maybe i will try that.

---

### Post by bjorntj on 2009-04-20
Hmmm... And by "run a java script" you mean? javascript has nothing to do with java....


BTJ

---

### Post by gremlin12 on 2009-04-20
Here is the simple script i am trying to run:

/* HelloWorld.java
   The classic first program
*/

public class HelloWorld {
  public static void main(String args[]) {
     System.out.println("Hello, World!");
  }//end method definition
}//end class definition

Does Java have nothing to do with this? I had thought Java was a language with useful applications for the web. Am I on the wrong track?

---

### Post by codeseer on 2009-04-20
Java is pretty darn annoying to encounter on the web. You're looking for C# or PHP. C# has similar syntax as Java and supports rapid development, without having to worry about garbage collection. PHP is popular and older though. If you plan to do only web development, then you should probably go with PHP. You'll want to setup what they call a XAMP to learn and test with, where the A stands for Apache, M stands for MySQL and P stands for PHP.

If you followed that tutorial I linked for Java, step 5 is where it should have fixed all your path problems.

---

### Post by gremlin12 on 2009-04-20
Well, it may not be the best choice but I thought it might be a place to start. However, it doesn't look I am going to be able to get it to work.

---

### Post by codeseer on 2009-04-20
> **gremlin12 said:**
> Well, it may not be the best choice but I thought it might be a place to start. However, it doesn't look I am going to be able to get it to work.

Web development is a lot to learn. If you're just looking to setup a website, go with something that you can just throw on a server and configure.

---

### Post by gremlin12 on 2009-04-20
ok, but i want to have an understanding of the basics. Just to know a little bit about how things work. I feel so illiterate. I've been learning XHTML and CSS...  I thought Java would be a good next step...

---

### Post by brunogirin on 2009-04-20
Java is a compiled language, not a scripting language, so you have to compile your code first and then run it. Go to the directory where you have your HelloWorld.java file and run the following:

```
javac *.java
```

This should produce a file called HelloWorld.class, which is your compiled program. Then you can run it this way:

```
java -classpath . HelloWorld
```

If you have a problem or error message with any of the above commands, post them here and I'll help you out.

If you are serious about learning Java, I suggest you install a Java IDE such as Eclipse or NetBeans. However, it's good to learn how to compile and run a program from the command line first.

---

### Post by gremlin12 on 2009-04-20
Thanks :)  I did what you suggested, here is the result:

mark@mark-laptop:~$ javac /home/mark/java/HelloWorld.java
mark@mark-laptop:~$ java -classpath . HelloWorld
Exception in thread "main" java.lang.NoClassDefFoundError: HelloWorld
Caused by: java.lang.ClassNotFoundException: HelloWorld
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: HelloWorld. Program will exit.


I did install the NetBeans and got it to work that way...but I would like to be able to do it the simple way.Thanks for your help :)

---

### Post by brunogirin on 2009-04-20
> **gremlin12 said:**
> Thanks :)  I did what you suggested, here is the result:

mark@mark-laptop:~$ javac /home/mark/java/HelloWorld.java
mark@mark-laptop:~$ java -classpath . HelloWorld
Exception in thread "main" java.lang.NoClassDefFoundError: HelloWorld
Caused by: java.lang.ClassNotFoundException: HelloWorld
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: HelloWorld. Program will exit.


I did install the NetBeans and got it to work that way...but I would like to be able to do it the simple way.Thanks for your help :)

OK, so verify that after you run the javac command, you have a file called HelloWorld.class in the directory /home/mark/java. Then run the following:

```
java -classpath /home/mark/java HelloWorld
```

The thing is that Java needs you to tell it where to find the .class files when you start it up. You can have .class files in a sub-directory if you use packages but that's slightly more complicated.

---

### Post by gremlin12 on 2009-04-21
It worked!!!  :D  I assume "classpath" tells the computer to find the path to the class file.

Thanks, Brunogirin, I appreciate your help!

---

### Post by brunogirin on 2009-04-21
Nearly. As usual with computing, it's a bi more complicated than that :-) classpath tells the java runtime where the root of the class hierarchy is. This is because classes can be managed in packages so you can have sub-directories. The classpath option takes a colon delimited list of directories and jar files.

So, if you want to have a similar example in a package, create the file HelloWorldInMyPackage.java in /home/mark/java/mypackage:

```

package mypackage;

public class HelloWorldInMyPackage {
  public static void main(String argv[]) {
    System.out.println("Hello World in my package!");
  }
}

```

Then compile the code:

```
javac `find /home/mark/java -name "*.java" -print`
```

This will tell the compiler to compile all files that have a name that ends in .java and that are in the /home/mark/java directory or a sub-directory. Then run it:

```
java -classpath /home/mark/java mypackage.HelloWorldInMyPackage
```

Note that by doing this, you have now compiled two classes in different packages so you can also run the previous example as you did earlier:

```
java -classpath /home/mark/java HelloWorld
```

What you normally do though is separate java source from class files so that you can easily remove all class files and recompile. What I normally do is have a directory called 'src' where I put the source and one called 'build' where I put the compiled code. In your case, you could have a directory called /home/mark/java/src and one called /home/mark/java/build, move all the .java files to the first one, delete all .class files and run the compiler again:

```
javac -d /home/mark/java/build `find /home/mark/java/src -name "*.java" -print`
```

As explained in the help, the -d option "Specify where to place generated class files" when running the compiler. If you do that, you will notice that the compiler has reproduced in /home/mark/java/build the directory hierarchy that you had in /home/mark/java/src. You can then run your example by specifying the build directory as the classpath:

```

java -classpath /home/mark/java/build HelloWorld
java -classpath /home/mark/java/build mypackage.HelloWorldInMyPackage

```

Try to get that to run and if you get any errors, post them here.

---

