---
title: "PHP tag bug?"
date: 2008-05-05
forum: Forum Feedback &amp; Help
---

### Post by amingv on 2008-05-05
I just posted this somewhere in the forums and noticed something...
Is this a bug on the PHP tags? (Notice where the colors start)

[PHP]#include <iostream>
#include <string>

int main(){
    int number;
    std::string message;
    
    std::cout << "Insert any number less than ten\n";
    std::cin >> number;
    std::cin.ignore();

    /*It works like this:
    variable = (condition) ? value_if_true : value_if_false;*/
    message = (number < 10) ? "It's less than ten\n" : "It's not less than ten\n";
    
    std::cout << message;
    
    return 0;
    
    /*Notice that I type the condition with spaces for clarity; but it would be legal
    to write message=(number<10)?"It's less than ten\n":"It's not less than ten\n";
    that's why a confection such as <? cannot be allowed.
    You cannot overload this operator either, so there's not much choice left.
    
    One has to admit, though, that it's shorter than writing
    
    if (number < 10) {
        message = "It's less than ten\n";
    }
    else {
        message = "It's not less than ten\n";
    }
    */
}[/PHP]
Now the code without the last comment:

[PHP]#include <iostream>
#include <string>

int main(){
    int number;
    std::string message;
    
    std::cout << "Insert any number less than ten\n";
    std::cin >> number;
    std::cin.ignore();

    /*It works like this:
    variable = (condition) ? value_if_true : value_if_false;*/
    message = (number < 10) ? "It's less than ten\n" : "It's not less than ten\n";
    
    std::cout << message;
    
    return 0;
}[/PHP]

It seems that (very much like g++) it doesn't like the <? combination, parsing confusion with something like:

<?php echo $PHP_SELF;?>

comes to mind... Did someone forget to sanitize their input? :)

Anyway, just a heads up...

---

### Post by LaRoza on 2008-05-05
php tags support syntax highlighing for C like languages mostly, but it also is specifically for php. PHP is often mixed with XHTML, and the syntax highlighting doesn't work for XHTML and is thus disabled. Editors do this, like gedit. 

I don't see any problems with it.

Without the <?...?>, it seems to assume all the code is PHP, which makes sense to me.

---

### Post by amingv on 2008-05-05
So I guess it can't be helped... Oh well.

---

### Post by LaRoza on 2008-05-05
> **amingv said:**
> So I guess it can't be helped... Oh well.

Its behavior makes sense.

---

### Post by amingv on 2008-05-05
> **LaRoza said:**
> Its behavior makes sense.

I understand; I just expected there could be something like, say, CDATA in XML, but it really doesn't matter if everything falls within normal behaviour. (That, and I believed PHP was just a misleadingly-named code tag, not an actual PHP specialized entity).

---

### Post by LaRoza on 2008-05-05
> **amingv said:**
> I understand; I just expected there could be something like, say, CDATA in XML, but it really doesn't matter if everything falls within normal behaviour. (That, and I believed PHP was just a misleadingly-named code tag, not an actual PHP specialized entity).

It is built for actual php code. PHP has a C/Perl like syntax, and the rules it follows allow it to give logical colouring to most languages that have a C like syntax. Even Python and Ruby to a large degree.

---

