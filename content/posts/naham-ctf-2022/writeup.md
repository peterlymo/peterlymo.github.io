---
title: "Nahamcon CTF 2022"
date: 2019-03-10
# weight: 1
aliases: ["/naham-ctf-2022"]
# tags: ["first"]
author: "Peter Lymo"
# author: ["Me", "You"] # multiple authors
url: "/writeup/nahamcon/"
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Desc Text."
canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
ShowWordCount: true
ShowRssButtonInSectionTermList: true
UseHugoToc: true
cover:
    image: "<image path/url>" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
editPost:
    URL: "https://github.com/peterlymo/peterlymo.github.io/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---

THE COMPETITION ORGANIZED BY JOHN HAMMOND WITH MANY SPONSORS

## CHALLENGES
### JOHNKS
| Name | Points | Authored By |
| -------- | -------- | -------- |
| johnks     | 500     | birch#9901     |

---
**Description**

![](https://i.imgur.com/VFT0m4g.png)

This is Forensic challenge

**solution**

i downloaded a png file and i can see a john Hammond pic and some stock values but the discription saying "Rising rising in height" so what if i increase the height of picture?



![](https://i.imgur.com/dC9Mhnk.png)



**using tweak png to edit image height**

![](https://i.imgur.com/86jUVSb.png)

then boom!!!
we get flag 

![](https://i.imgur.com/3FwI8Iz.png)

DONE!!!


---



### A WILD WIDE
| Name | Points | Authored By |
| -------- | -------- | -------- |
| A wild Ride     | 500     | Kkevsterrr#7469    |

---
**Description**

![](https://i.imgur.com/PWvAs18.png)


This is Forensic challenge

**solution**

i downloaded a zip file and it procteted but inside there bunch of file with extension gpx


![](https://i.imgur.com/W8pgVE2.png)

after some googling i found that gpx is "is simply a text file with geographic information such as waypoints, tracks, and routes saved in it." so its like MAP point uhhh well

but the zip is Protected so i have to crack first

![](https://i.imgur.com/HZsNxHw.png)

pasword:crackme


so its time to get the flag from those file where inside contain xml code

![](https://i.imgur.com/kQm3ghD.png)

 so its dead end , i need to open those file so i must find the right tool for this. i just googled how to open but many tools was able to open one by one but not in group until i found https://gpx.studio/
 
 then after loading files. we get flag
 
![](https://i.imgur.com/HFxHUNg.png)





---


### STEAM LOCOMOTIVE
| Name | Points | Authored By |
| -------- | -------- | -------- |
| Steam Locomotive     | 500     | JohnHammond#6971     |

---
**Description**

![](https://i.imgur.com/rvUrp7B.png)


This is Miscellaneous challenge

**solution**
after clicking **start challenge** i was given a ssh credentials then when i login i see train running on terminal then connection is closed


![](https://i.imgur.com/LAIzyb4.png)

so i know to solve this type of challenge i need ssh tool that automate a login and execute commands before a server command do, then i used **sshpass** to do that

I run

![](https://i.imgur.com/8yfvglw.png)

DONE!! EAZY PIIIEZY





---


### CEREAL
| Name | Points | Authored By |
| -------- | -------- | -------- |
| Cereal     | 500     | BusesCanFly#2237     |

---
**Description**

![](https://i.imgur.com/E1pKzxh.png)

This is Hardware/RF challenge

**solution**

i downloaded a file and it called mystery.sal . so here its about looking for extension name . i just found that there tool called **logic analyzer** can open that


![](https://i.imgur.com/C6Cv9uW.png)

well on topi can see weird characters

![](https://i.imgur.com/bPHH1JS.png)

i had to zoom out so i can see clear
boom flag is there

![](https://i.imgur.com/PU6ukwN.png)

EAZY PIIEZY


---

**so android challenge its about doing code review you just need to know where sensitive data are stored or what function pull important data and so on. so i just wanted to give a try here are challenges i solved and learning something new**

### OTP VAULT
| Name | Points | Authored By |
| -------- | -------- | -------- |
| otp vault     | 500     | congon4tor#2334     |

---
**Description**

![](https://i.imgur.com/b2wdtgj.png)


This is Mobile challenge

**solution**

i downloaded a file and its apk which means its android file

installed a app and its 

![](https://i.imgur.com/aLYNLyj.png)

so i am supposed to enter a correct code which i dont know yet

i fired a jdx tool and start to look for source
i started with androidmanifest.xml

![](https://i.imgur.com/7ARHfsT.png)

activity running is **MainActivity** so lets check it



```
package com.otpvault;

import com.facebook.react.ReactActivity;
import com.facebook.react.ReactActivityDelegate;
import com.facebook.react.ReactRootView;

/* loaded from: classes.dex */
public class MainActivity extends ReactActivity {
    @Override // com.facebook.react.ReactActivity
    protected String getMainComponentName() {
        return "OTPVault";
    }

    @Override // com.facebook.react.ReactActivity
    protected ReactActivityDelegate createReactActivityDelegate() {
        return new MainActivityDelegate(this, getMainComponentName());
    }

    /* loaded from: classes.dex */
    public static class MainActivityDelegate extends ReactActivityDelegate {
        public MainActivityDelegate(ReactActivity reactActivity, String str) {
            super(reactActivity, str);
        }

        @Override // com.facebook.react.ReactActivityDelegate
        protected ReactRootView createRootView() {
            ReactRootView reactRootView = new ReactRootView(getContext());
            reactRootView.setIsFabric(false);
            return reactRootView;
        }
    }
}
```


looks like it built IN **react** my guess was there must some javascript vile outhere

so looking for **index.android.bundle** we can see some javascript code so i had to copy and put to beautifier so i can see clearly

![](https://i.imgur.com/GZFffjQ.png)


now after spent time looking for something good , finnaly i found interested function under line **31975** (daaamn so many lines to look, but sometimes you can search for some keyword like "flag" and that what i did after struggling)

![](https://i.imgur.com/8dElrxe.png)


**analyzing the code, **

seems the flag come from web server which use basic bearer authorization so my gues is i dont need to bypass the OTP app to get flag so i copied the url put to web

**first shot**

![](https://i.imgur.com/7OGWrKY.png)

ohh no!! i just remember there /flag path lemme try itt

**second shot** 

![](https://i.imgur.com/2j3RZdc.png)

ohh are we go again , i just remember there bearer token outhere

**third shot (using burp)**


![](https://i.imgur.com/scy9zC5.png)


BOOOM we get flag!!!

**EAZY PIIZY**


---


### CLICK ME
| Name | Points | Authored By |
| -------- | -------- | -------- |
| Click Me     | 500     | M_alpha#3534     |

---
**Description**

![](https://i.imgur.com/LU7lGH5.png)
 
This is Mobile challenge

**solution**

i downloaded a file and its apk which means its android file

installed a app and its 

![](https://i.imgur.com/NVLBLw4.png)

so i am supposed to click until flag pop and i dont know how many times, could be 19029292939393 times or whetever but must be a larger number which will took me forever.

so lets view source code using jadx tool

starting with androidmanifest

![](https://i.imgur.com/0kg5OZh.png)

we can see activity we are dealing with it its MainActivity, so lets check it out

we spoted this code


    public final void cookieViewClick(View view) {
        int i = this.CLICKS + 1;
        this.CLICKS = i;
        if (i >= 13371337) {
            this.CLICKS = 13371337;
        }
        ((TextView) findViewById(C0574R.C0577id.cookieCount)).setText(String.valueOf(this.CLICKS));
    }

    public final void getFlagButtonClick(View view) {
        Intrinsics.checkNotNullParameter(view, "view");
        if (this.CLICKS == 99999999) {
            Toast.makeText(getApplicationContext(), getFlag(), 0).show();
            return;
        }
        Toast.makeText(getApplicationContext(), "You do not have enough cookies to get the flag", 0).show();
    }

well seems like even we automate the action, one the click become greater or equal to 13371337 it will be assigned with that number everytime, so we wont be at 99999999 (am not sure but that what is my understand about the code)

continue ...

i can see if the click become 99999999 i get the flag from method called **getFlag**() .

ohh getFlag() is interested!!
so then adventure beginn , the fact is i want to try a tool called frida and this is a time to give a try

i setup Frida ,

android emulator or rooted phone (i used genymotion)

i started frida server

![](https://i.imgur.com/oRSV4cK.png)

its running !!!!

![](https://i.imgur.com/83jplaw.png)

my app its there so here is a big picture, we need to write a javascript code that will hook getFlag() method and give to us:

after **hours** i finaly come with this short payload that do the magic

```
//author: malwarepeter 29/04/2022

Java.perform(function(){
  var click = Java.use("com.example.clickme.MainActivity");

  var run = click.$new();
  var returnvalue = run.getFlag();
  console.log("");
  console.log("Flag: " + returnvalue);
});
```
BOOM!!! so excited , i get flag

![](https://i.imgur.com/nHikf6R.png)

so much fun on this! but end up learning something new, hope i will play around more with frida


---


---

REFERENCES

https://blog.ikuamike.io/posts/2020/razictf-chasingalock-writeup/

https://alyagomaa.github.io/blog/Using-Frida-to-call-unused-android-methods/
