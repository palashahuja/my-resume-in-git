# Track Palash's resume in git

## How to track applications
I don't always customize my resume for each application, but I still want a way to track what jobs I applied for.
This was hard to do for two reasons:

1. Appending git messages and git tags wasn't great for tracking job requirements
1. Branching was harder to remember/use without a regular "main" branch

Whenever I apply to a role I export the job description—print to pdf—to the repo and commit it as jd.pdf.
This lets me always reference what job I applied for when, and gives me a permanent record of the job description.

Job postings only exist online for a short time so keeping a record has been very helpful.

This doesn't work well for jobs I've applied for without a job description (direct apply to manager), jobs I've applied to via LinkedIn "Easy Apply", or jobs I've applied to via my phone.

What I do in those cases is:

* If I apply directly do the hiring manager I email myself a note of who I emailed and the role title to add to a jd.txt file
* If I'm on mobile, I export the page to a PDF and email it to myself to add to the repo later
* If I apply through LinkedIn Easy Apply I save the link and later add it to jd.txt

This helps me track the majority of jobs I apply for in git with consistent file naming.

I haven't been using LinkedIn Easy Apply for very long, and as far as I can tell job posting links don't expire.
Someone please let me know if they do expire or you know a better way to export a LinkedIn job posting.

## Branch management

I have branches for different job families, and companies.
The main branch is usually a generic form of my current resume format.
I only commit to main when I change how my resume looks or use a new tool to generate it.

For example, when I apply at a new company, I make a branch.
Some companies I only apply to one job, others I apply to many jobs.

Sometimes those jobs are all a similar type of role (e.g. software engineer), but sometimes they're different job families (e.g. manager, SRE).
Keeping separate branches for each job type let's me keep relevant information in one branch and cherry pick the resume into the company branch when I apply for a role.

A typical application workflow at a new company might look something like this.

```
git checkout role-sre
git switch -C cool-co
vim "Justin Garrison.html"
<Make edits>
just pdf # generate PDF file
just jd "https://example.com/job" # download job description into jd.pdf
git add .
git commit -m "Apply: SRE job at cool-co"
```

If I find more jobs at "Cool Co." I can re-use this resume with an updated jd.pdf file and add a new commit for the new role.
