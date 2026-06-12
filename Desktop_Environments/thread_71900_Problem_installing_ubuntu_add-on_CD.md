---
title: "Problem installing ubuntu add-on CD"
date: 2005-10-04
forum: Desktop Environments
---

### Post by linuxeiro on 2005-10-04
Hello, I am relatively new to Linux and Ubuntu, which I've been using for some months. Since I am happy with Ubuntu, I am trying to install it in another computer without broadband, son I downloaded and burned the Add-on CD and followed the instructions for newbies on [http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/)  and ubuntuforums.org (tips and tricks):
Copy Ubuntu-Add-on CD to harddrive
sudo sh /media/cdrom0/install.sh
Install applications from Ubuntu Add-on CD after copying it hd
sudo sh $HOME/Downloads/ug-install.sh
Optional - Install all applications on cd unattended
sudo sh $HOME/Downloads/ug-install.sh -auto

When I type the first line of instructions in the terminal, it works fine and copies ubuntu to my harddrive on /root/Dowloads
But when I type any of the other two lines of instructions, it repeatedly sends me this message of error:
# sudo sh $HOME/Downloads/ug-install.sh -auto
sh: /root/Downloads/ug-install.sh: No such file or directory
# cd /root/Downloads/ub-install.sh
bash: cd: /root/Downloads/ub-install.sh: No such file or directory

I have I problem here since I don't know how to run the script! I have looked into the folder where the cd has been copied: its /root .Inside the "root" folder there is another folder named "Downloads", and another 3 files named ug-install.sh , dbootstrap_settings and install-report.template. So the script file exists in fact, but not inside the "Downloads" folder but in "root". How should I write the instruction in the terminal in order to install the CD? Thank you very much

---

### Post by Ampersand on 2005-10-04
you just need to use the path that it's been copied to. So in this case, the command would be 'sudo sh /root/ug-install.sh'.

---

### Post by linuxeiro on 2005-10-04
Thank you, Ampersand, it worked with sudo sh /root/ug-install.sh   :smile:    Thanks a lot indeed!!

---

