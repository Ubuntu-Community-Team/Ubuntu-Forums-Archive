---
title: "CGI Proxy and SSH"
date: 2009-05-10
forum: General Help
---

### Post by ashcarr on 2009-05-10
Hi, I have [cgi proxy]("http://www.jmarshall.com/tools/cgiproxy/") on my server and its working a treat. However, I can't get SSH to work. Both modules listed on that page are installed as querying them returned a version number. Port whatever it is, 403 I think, is forwarded to my machine. Now, I'm a complete newbie to perl and ssh, all I do is make things look pretty in photoshop and flash and make html/css webpages.

When I add the https to the URL, I get 
> 
Failed to Connect

The connection was refused when attempting to contact address.ath.cx.

Though the site seems valid, the browser was unable to establish a connection.


    *  Could the site be temporarily unavailable? Try again later.

    *  Are you unable to browse other sites?  Check the computer's network connection.

    *  Is your computer or network protected by a firewall or proxy? Incorrect settings can interfere with Web browsing.

Ditto with using an internal IP instead of the domain.

Now, apaprently having those 2 modules installed should just work as that cgi script apparently looks at the default path to the modules, which I installed in the default place.

Any information would be greatly appreciated, the problem is most likely me being stupid, but hey, we all start somewhere!



Another issue I am having is that I am having to use the URL encoding to make sure that the displayed URL shows something else, not the actual site as the filtering system I am working around checks the URL for anything. A prime example being facebook.
Now, the built in ones work pretty darn well, but they don't seem to be right, as the decoding does not completely unscramble it:
```

sub proxy_encode {
    my($URL)= @_ ;
    $URL=~ s#^([\w+.-]+)://#$1/# ;                 # http://xxx -> http/xxx
** [COLOR=Red]   $URL=~ s/(.)/ sprintf('%02x',ord($1)) /ge ;   # each char -> 2-hex[/COLOR]**
#    $URL=~ tr/a-zA-Z/n-za-mN-ZA-M/ ;              # rot-13

    return $URL ;
}

sub proxy_decode {
    my($enc_URL)= @_ ;

#    $enc_URL=~ tr/a-zA-Z/n-za-mN-ZA-M/ ;        # rot-13
** [COLOR=Red]   $enc_URL=~ s/([\da-fA-F]{2})/ sprintf("%c",hex($1)) /ge ;[/COLOR]**
    $enc_URL=~ s#^([\w+.-]+)/#$1://# ;           # http/xxx -> http://xxx
    return $enc_URL ;
}

```Example, navigating to facebook with this gets:
> Couldn't find address for [www.úÎbook.com:]("http://www.%C3%BA%C3%8Ebook.com:") Connection timed outSo it isn't quite perfect.
Does anyone have a encode + decode that works perfectly? I only need something ridiculously simple, just so that it doesn't show the actual URL.

---

