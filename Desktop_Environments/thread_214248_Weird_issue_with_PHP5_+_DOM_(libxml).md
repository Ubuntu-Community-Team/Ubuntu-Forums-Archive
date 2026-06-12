---
title: "Weird issue with PHP5 + DOM (libxml)"
date: 2006-07-12
forum: Desktop Environments
---

### Post by SNo0py on 2006-07-12
Hey out there,
I'm trying to solve an issue for about 2 days now and it's driving me crazy. Basically I want to run the Webservice Helper from [http://jool.nl/new/index.php?file_id=1](http://jool.nl/new/index.php?file_id=1) , but it's always giving me warnings:

Warning: DOMElement::setAttribute() [function.setAttribute]: No such attribute 'xmlns:soap' in ... on .../WSDLStruct.class.php on line 116

Same for the lines below. And yes, I checked them out and they are working fine on another system (Redhat). The PHP-version is the same (5.1.2), the only difference I could find was the libxml version.

Working: 2.6.20
Non-working: 2.6.26

So is there a way to "downgrade" locally or does anyone have an idea why this is not working with a default installation of Ubuntu 6.06 LTS?

Any hint is welcome,

thanks!

---

### Post by SNo0py on 2006-07-13
My quick hack to at least get it working was:

```
                //$this->doc = new domDocument();
                //$this->definitions = $this->addElement("wsdl:definitions",$this->doc);
                $this->doc = DOMDocument::loadXML(
                        '<wsdl:definitions xmlns="http://schemas.xmlsoap.org/wsdl/"
                                xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/"
                                xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/"
                                xmlns:wsdl="http://schemas.xmlsoap.org/wsdl/"
                                xmlns:xsd="http://www.w3.org/2001/XMLSchema"
                                xmlns:tns="http://schema.example.com"
                                targetNamespace="http://schema.example.com">
                        </wsdl:definitions>'
                );
                $this->definitions = $this->doc->firstChild;
```

In the file WSDLStruct.class.php and commenting out the non-working lines. That way the DOM Extension does not complain about missing namespaces... Weird.

---

### Post by SNo0py on 2006-07-13
This bug seems to be related to [http://bugs.php.net/bug.php?id=37790](http://bugs.php.net/bug.php?id=37790) 

Where should I report this so it gets fixed in Ubuntu?

---

