---
title: "Trying to Find a &quot;Macro&quot; or &quot;SendKeys&quot; app"
date: 2007-08-21
forum: Desktop Effects &amp; Customization
---

### Post by zigx on 2007-08-21
Hey Guys,

I am trying to find an application that i can use to send keystrokes to other applications.

For example in windows i used to use a program called typeitin ( [http://www.wavget.com/typeitin.html](http://www.wavget.com/typeitin.html) )

In TypeItIn all you do is create a button that when clicked executes a predefined (recorded) set of keystrokes.

This makes it super easy for me to fill in forms, or do repetitive tasks that are part of my day job.

Does anyone have any suggestions?  I use Gnome.

thank you very much

Edit: I just realized i might have posted this in the wrong area... sorry to mods! :)

---

### Post by RasmusMH on 2007-08-25
Maybe this is the wrong place but i do have a sollution although not the one you would expect. I used a similar program on windows, and kinda missed on linux. Fortunately im pretty good at java so my solution is this:
import java.awt.Robot;
import java.awt.event.KeyEvent;
class SendKeyDevice{
public static void main(String[] args){
try{
robot = new Robot();
sendKey(KeyEvent.VK_U);
sendKey(KeyEvent.VK_I);
sendKey(KeyEvent.VK_D);
sendKey(KeyEvent.VK_TAB);
sendKey(KeyEvent.VK_P);
sendKey(KeyEvent.VK_W);
sendKey(KeyEvent.VK_D);
sendKey(KeyEvent.VK_ENTER);
}catch(AWTException exc){}
}
private static Robot robot;
        private static void sendKey(int k){
                robot.keyPress(k);
                robot.keyRelease(k);
        }

}

enter that into a file called SendKeyDevice.java .. compile it using almost any version of sun javac and run it with almost any version of sun java by typing: java SendKeyDevice in the correct directory. This has the effect of typing: "UID<tab>PWD<enter>" in any active window. If you create a shortcut that starts the program in the background it will perform on the active window. Works for me.

---

### Post by zigx on 2007-08-28
> **RasmusMH said:**
> Maybe this is the wrong place but i do have a sollution although not the one you would expect. I used a similar program on windows, and kinda missed on linux. Fortunately im pretty good at java so my solution is this:
import java.awt.Robot;
import java.awt.event.KeyEvent;
class SendKeyDevice{
public static void main(String[] args){
try{
robot = new Robot();
sendKey(KeyEvent.VK_U);
sendKey(KeyEvent.VK_I);
sendKey(KeyEvent.VK_D);
sendKey(KeyEvent.VK_TAB);
sendKey(KeyEvent.VK_P);
sendKey(KeyEvent.VK_W);
sendKey(KeyEvent.VK_D);
sendKey(KeyEvent.VK_ENTER);
}catch(AWTException exc){}
}
private static Robot robot;
        private static void sendKey(int k){
                robot.keyPress(k);
                robot.keyRelease(k);
        }

}

enter that into a file called SendKeyDevice.java .. compile it using almost any version of sun javac and run it with almost any version of sun java by typing: java SendKeyDevice in the correct directory. This has the effect of typing: "UID<tab>PWD<enter>" in any active window. If you create a shortcut that starts the program in the background it will perform on the active window. Works for me.

that is pretty awesome, thank you RasmusMH!

---

### Post by Satisfied w/o Micro$oft on 2008-02-10
I have a similar need -- but am not comfortable with a java based solution. Mainly, I have no experience with it -- and I find it hard to believe that there is not a existing application or gnome feature that will provide keystroke macro functionality. 

Any other solutions would be greatly appreciated...

---

### Post by 1comment on 2008-03-27
Atomato (currently only available from SVN, "svn co http://svn.gnome.org/svn/atomato/trunk/" should get the source), as far as I know, is meant to be a macro app. However, I have no idea how developed it is, and there doesn't seem to be much documentation...

 Workflow ( [http://www.kde-apps.org/content/show.php/WorKflow?content=43624](http://www.kde-apps.org/content/show.php/WorKflow?content=43624) ), which is KDE but possibly a little more developed.

(to be honest, i haven't used either, but they might be of help for ya)

---

