# Basic Starter Template

A small five-page HTML site about farming in middle Georgia. Use it to
practice the whole workflow — grab a template, clone it, edit it, push your
changes back, and put it live on the class server. No Python to write, no
Flask, no database. Just HTML and CSS.

## What's in it

```
public/                 Your website. Everything in here is public.
  index.html            Home — why middle Georgia grows what it does
  peaches.html          Peaches
  pecans.html           Pecans
  peanuts.html          Peanuts
  poultry.html          Poultry
  styles.css            Shared styling (one --brand color drives the theme)

Procfile                How the class server starts your site
requirements.txt        Tells the class server your project is Python
runtime.txt             Which Python version to use
```

Every page shares the same header, navigation, and stylesheet, so you can
change the look of the whole site in one file.

**Your work goes in `public/`.** The three files beside it are setup — you do
not need to understand them yet, and you should not edit them. Module 3 is
where you build them yourself and learn what each one does.

That split is not decoration. A web server hands out everything inside the
folder it is pointed at, so the folder it is pointed at should contain your
website and nothing else. Anything you keep *outside* `public/` — notes,
settings, passwords later in the course — is not on the internet. Putting a
password where the web server can reach it is one of the most common ways real
sites leak, and the folder layout is what prevents it.

## How to use it

1. Open the `public` folder and double-click `index.html`.
2. Open the project in your editor. Change some text on a page, or change the
   `--brand` color at the top of `public/styles.css`.
3. Save the file, then reload the browser tab to see your changes.

## How to put it on the class server

Your app on `iscs2.gcsu.edu` was created for you already. Its name is your
netid with the dots turned into dashes, plus `-quiz-1` — so if you sign in to
iscs1 as `ava.dente`, your app is `ava-dente-quiz-1`.

Do this once, in your project folder:

```bash
git remote add dokku dokku@iscs2.gcsu.edu:ava-dente-quiz-1
```

Use *your* app name, not `ava-dente-quiz-1`. Then, every time you want the live
site to catch up with your edits:

```bash
git add .
git commit -m "My first edits"
git push origin main    # your code, to GitHub
git push dokku main     # your site, to the class server
```

Those last two lines are two different places. `origin` is GitHub, where your
work is graded and backed up. `dokku` is the server that actually runs the site.
Pushing to one does nothing to the other.

Your site is at `https://iscs2.gcsu.edu:<your-port>` — the push prints the URL
when it finishes, and **Deployments** in the course sidebar on iscs1 lists it too.

## If something goes wrong

| What you see | What it means |
|---|---|
| `Permission denied (publickey)` | Your SSH key is not registered yet. See Module 1 Lesson 5. |
| `repository ... does not exist` | Check the app name — dashes, never dots. |
| `Everything up-to-date` but the site is unchanged | You committed nothing. Run `git add .` and `git commit` first. |
| The push worked but the page looks old | Hard-reload the browser tab. |

That's the whole exercise.
