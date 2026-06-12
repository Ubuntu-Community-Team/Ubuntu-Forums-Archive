---
title: "help"
date: 2009-03-19
forum: General Help
---

### Post by jerryt on 2009-03-19
I want to appolgize to evryone for my last post, I never thought anyone owed me anything and never intented for it to be like that,the only thing was trying to find out is symantic packages because, the language on is so high tech for me i don't know what the packages is, add/remove i have a fair understanding on,also what i was trying to do is download, skype and desktop weather.

Now i need so advise on the forums, see i have posted some messages and then after i log off the forum and the next day log in i can't find what i posted, guess im a computer dummie, if someone could gide me a little bit, it would be deeply appreciated.

---

### Post by lindsay7 on 2009-03-19
Ok, first, it would be helpful if you discribe what help you need in your subject line. 

To find your past posts go to "Search" on the menu bar ( user cp, forum help, forum counsel, new posts, search) then go to the bottom and click on "find all your posts".

You will find Skype in the Synaptic package manager. Make sure the you choose "all" in the colume on the left.  Just click on it and it will download. Then look for it under Applicatons/net on your top menu bar.

Packages are software programs. You can find them in the Synaptics area or the add/remove under applications on the menu bar. Again click on all applications at the top when you search and that way your search will be for all availible software from all sources. When you click on an item there will be a discricption shown at the bottom. If you want more information on it you can look for it on the web. Experiment with packages. They are free and you can remove them easily if you want.

---

### Post by zvacet on 2009-03-19
How to find your posts/threads? When you login to forum you will see **search**and click on it and in dropdown menu you can choose between **find your posts** and **find your threads**.

To install Skype you have to do this:applications>accessories>terminal
and type 

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```
 or 

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```

if you use Ubuntu 8.04.After that also in terminal 

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Now you can install skype by typing 

```
sudo apt-get install skype
```

Other way is to go to the system>admin>synaptic>in search box type skype and when you find it click on the box on the left and mark it for install.

Please,in future use more descriptive titles to make it easier to know what your problem is and what kind of help you need.I hope you will enjoy Ubuntu!

---

