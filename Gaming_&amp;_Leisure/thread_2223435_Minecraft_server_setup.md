---
title: "Minecraft server setup"
date: 2014-05-11
forum: Gaming &amp; Leisure
---

### Post by Bridger_B on 2014-05-11
Following this.  
[http://youtu.be/rilO2R0WFLI?t=2m24s](http://youtu.be/rilO2R0WFLI?t=2m24s) 

I don't know what he does with his different windows. Where does he type the next step? sorry but it is a little confusing for a beginner.

---

### Post by staticn0de on 2014-05-12
> **Bridger_B said:**
> Following this.  
[http://youtu.be/rilO2R0WFLI?t=2m24s](http://youtu.be/rilO2R0WFLI?t=2m24s) 

I don't know what he does with his different windows. Where does he type the next step? sorry but it is a little confusing for a beginner.

Hi there,

I am not sure what you are asking but I will try to explain what he is doing.

He has installed minecraft server on "something" (could be a virtual machine, physical server and so on) and he is controling it by using another computer which is connected via SSH. For example, I could install minecraft on my HP N54L microserver which has no monitor and remote in via my laptop and setup / manage the server.

Now, say I remoted in via SSH to the HP N54L and started the minecraft server, if I shut down my laptop or lose the connection the minecraft server will also stop as it is running as part of my active SSH session.

He has installed the application 'screen' in order to manage this. This allows the user to have 'sessions' which can be maintained independently of the SSH connection.

For example, I remote in via SSH to my N54L server, launch a screen session and then start the server. I can now disconnect the screen session from the display and then disconnect my SSH session. The minecraft server will still be running.

You can find some great tutorials on screen or install it via apt-get install screen and then use man screen.

---

