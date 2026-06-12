---
title: "Creating a Playlist.com Widget"
date: 2009-03-13
forum: Desktop Environments
---

### Post by ChadAragorn on 2009-03-13
I was looking for a way to do this but couldn't find a "how to" so I set about doing it on my own. I'm a Linux NooB but was able to figure it out and I am pleasantly pleased with the end result. 

[[IMG]http://img9.imageshack.us/img9/3174/playlistwidget.png[/IMG]](http://img9.imageshack.us/my.php?image=playlistwidget.png)

Now how did I do this....

First off, I'm running **ubuntu 8.10 Intrepid x64**. So the following steps may or may not work with your distro.
You need to have **compizfusion** on your system and need to have the widget layers enabled. Like this
[[IMG]http://img6.imageshack.us/img6/7440/screenshot9d.png[/IMG]]("[URL=http://img6.imageshack.us/my.php?image=screenshot9d.png)"][[IMG]http://img6.imageshack.us/img6/7440/screenshot9d.png[/IMG]](http://img6.imageshack.us/my.php?image=screenshot9d.png)[/URL]

This website gave me the idea **_[http://tombuntu.com/index.php/2008/04/08/google-gadgets-and-web-widgets-on-your-desktop-with-screenlets/]("http://tombuntu.com/index.php/2008/04/08/google-gadgets-and-web-widgets-on-your-desktop-with-screenlets/")_**

Get the **Screenlets** application thru the add/remove section. 
Next I had to run the following code in the terminal: **sudo apt-get install python-gnome2-extras**. 
Once this is finished you'll be ready to begin creation of your [**_Playlist.com_**]("http://www.playlist.com/user/register") account if you don't already have one. 
Once you have the account created then you need to click on the "**get playlist code**" button located at the bottom of your playlist.

*
You need to choose option **E**, select your playlist. Next, choose your options and click **get code**. Should look like this: [[IMG]http://img7.imageshack.us/img7/2851/likethisb.png[/IMG]](http://img7.imageshack.us/my.php?image=likethisb.png)

Now you will need to edit this code a little bit before it is ready. First where it says "**width:450px**" change that to say "**width:435px**". Next the portion of code, at the very end of the coding, that says, **"</object> <br/> <a href="http://www.profileplaylist.net"><img src="http://www.profileplaylist.net/mc/images/create_black.jpg" border="0" alt="Get a playlist!"/></a> <a href="http://www.mysocialgroup.com/standalone/60558993" target="_blank"><img src="http://www.profileplaylist.net/mc/images/launch_black.jpg" border="0" alt="Standalone player"/></a> <a href="http://www.mysocialgroup.com/download/60558993"><img src="http://www.profileplaylist.net/mc/images/get_black.jpg" border="0" alt="Get Ringtones"/></a> </div>"**, is not needed and only creates advertisement buttons; don't want those mucking up your player, so delete it from your code. Now that you have your final code you need to **copy** the code.

Next open the **screenlets** application.[[IMG]http://img14.imageshack.us/img14/3010/screenshot10.png[/IMG]](http://img14.imageshack.us/my.php?image=screenshot10.png)

Choose **Install**-- **Convert Web Widget**-- Paste your code in the step 2 box
Name your Widget and click OK. You should see it appear in the list of available screenlets. 
Click on your new screenlet and then click the **launch/add** button. If you don't see your widget pop up, try pushing **F9**, this gives you access to the widget layer. Move your new widget around and place it where you'd like it to stay. Click the little wrench on the widget and you can change some settings, I chose to have mine locked in place, and stuck to the background. Your widget, do what you'd like. You can also, in the screenlets app, determine if the playlist should start on login if you'd like. Otherwise, you must launch it each time you logon. You will need to launch it each time you update your playlist though; that way the changes take place. Well there you have it, a way to play music, from the INTERNET, on your desktop, without being logged into a website. 

Also, you can use a custom image for your player if you'd like to go that route, find the image you want, use **gimp** or other program to scale the image to 435x270, save it. Use [imageshack]("http://www.imageshack.us/") to host it. Copy the directlink to the file, and when, back before you copied the code for your playlist, choose custom background, paste your direct link in there, get code, and start with guide again from the *. Hope this helps some people out.:P****

---

