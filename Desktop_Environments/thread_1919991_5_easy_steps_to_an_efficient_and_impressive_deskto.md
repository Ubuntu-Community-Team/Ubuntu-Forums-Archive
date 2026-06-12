---
title: "5 easy steps to an efficient and impressive desktop experience"
date: 2012-02-03
forum: Desktop Environments
---

### Post by Mahkoe on 2012-02-03
Note: I am using Ubuntu 10.10 (I can't stand the later versions), so a lot of these settings may not work, or some of the programs may not be available in later versions of Ubuntu. For the best possible chance, select Ubuntu Classic in the login menu. Also, these settings are configured for the use of a mouse. This will probably make everything worse if you're using a touchpad or a wacom tablet.

**Step 1:**
Install compizconfig and wmctrl by running this command:
```
sudo apt-get install compizconfig-setttings-manager wmctrl
```

**Step 2:**
Go into compizconfig (System -> Preferences -> CompizConfig Settings manager) and click "Window Management" in the pane on the left, under "Categories". Click "Scale". There will be three lines labelled "Initiate window picker for all windows". One of them well have a small icon of a screen on its left. On the same line towards the right, click on the button that says "Disabled". This will give you a choice of screen edges. I recommend top right. What this will do is it will show you all your windows and allow you to choose the one you want every time your mouse pointer moves into the screen edge previously selected. It's very handing for quickly switching between applications.

**Step 3:** 
Click "Back" on the bottom left. Under "Category" in the pane on the left, click "all" and scroll up to the top. You should see a button labelled "Commands". Make sure it has a checkmark beside it. Copy this line into Command line 0:
```
wmctrl -r :ACTIVE: -b toggle,maximized_horz,maximized_vert
```
Now, hit the "Edge Bindings" tab. Click on the button labelled "Disabled" to the right of "Run Command 0" and select a screen edge. I recommend bottom left. Make sure it is not the one you just selected in Step 2. What this will do is maximize or unmaximize the active window every time your mouse pointer moves into the selected screen edge.

*[OPTIONAL]*
Go back to the "Commands tab" and paste this line into Command line 1:
```
wmctrl -c :ACTIVE:
```
Now, go back to the "Edge bindings" tab and click the button that corresponds to "Run Command 1". Select a different screen edge. I recommend bottom right. What this will do is close the active window every time your mouse pointer reaches the selected screen edge. I find this very useful, others will find this annoying and frustrating.

Just a quick tip, you can assign keyboard shortcuts and mouse click shortcuts as well, I am merely recommending the use of the screen edges, I find it's much more efficient.

**Step 4:**
Create a new file in your home folder. Name it whatever you want, I recommend you start the name with a ".", that way it will become hidden and you will never have to see it ever again. Paste this code into it:
```
#!/bin/bash
if [ `gconftool-2 -g /apps/nautilus/preferences/show_desktop` = "false" ] 
then
	gconftool-2 -s /apps/nautilus/preferences/show_desktop --type boolean true
else
	exec gconftool-2 -s /apps/nautilus/preferences/show_desktop --type boolean false
fi
```
Now, open a terminal window and type the following command, where .nameOfFile is replaced by the name of the file you just created:
```
sudo chmod +x .nameOfFile
```
This allows the program to run. Now, right click on your panel and hit "Add to Panel...". Ubuntu 11.04 and later users will want to see this link: [http://blog.mattwoodward.com/how-to-create-a-custom-launcher-in-unity-on-u](http://blog.mattwoodward.com/how-to-create-a-custom-launcher-in-unity-on-u). In the "Command" section of the the window that opens, type in the location of your file; it will be something like "/home/yourUsername/.nameOfFile". Any other customization is up to you. What this will do is toggle the visibility of your desktop icons. (No guarantees in 11.04 or later)

**Step 5:**
This is more for show than anything, but I love this. In the compizconfig menu, click "Effects" in the pane on the left, under "Categories". Check the box that corresponds to "Wobbly Windows". A window will pop up saying that you need to disable "Snapping Windows". Click the button labelled "Diable Snapping Windows" (don't worry, we'll work around this). Now, click on the button labelled "Wobbly Windows" and check the box for "Snap Inverted". What this does is it will automatically "snap" your windows to the screen edges and other windows, unless you hold the shift key while moving a window.

**Bonus:**
In compizconfig, click "Window Management" in the pane on the left under "Categories" and click "Resize Window". There will be line that says "Initiate window resize" beside an icon of a mouse. Click the button on the right. In the four buttons that say "Super" "Shift" "Ctrl" and "Alt", make sure only "Alt" is highlighted. In the dropdown menu beneath these buttons, select "Button 3" and hit "OK". A window may pop up saying something about disabling window menu. Click the button labelled "Disable Window Menu". This will resize windows if you hold alt and right-click and drag. I find this very useful.

Okay, that's it. I know not many people use 10.10 anymore, but this is for all the people who do; I don't think any of these work in later versions, but it's worth a try. Enjoy

---

