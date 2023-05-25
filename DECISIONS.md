
# DECISIONS


## DESIGN

· First I had to decide on the design of the pipeline as far as environments, extra components and deployment strategy goes.

· I had originally intended to have a TEST, STAGING and PRODUCTION env´s but had to skip STAGING due to time constraints.
  I also wanted to implement several extra components but also due to time constraints I thought it would be best to stick with a simple SENTRY integration for all env´s.
  As for my deployment strategy, at this point I had decided I wanted to deploy TEST & PROD to a DigitalOcean Docker server, so I proceeded to set that up on their platform.

## LOCAL TEST

· Once I had my rough plan, I first made sure I could build & run the webapp locally in Docker w/o making any changes.
  This was not the case, as the Postgres container was failing due to an incompatible versioning.
  The solution was to revert it from v14 to v13. Upon making this change, I verified everything was running smooth locally.

## IMPLEMENT
  
· At this point I started implementing my GitLab pipeline. 
  I was a bit confused as to how I would integrate Sentry as doing it via the .gitlab-ci.yml would mean that I would have to edit the requirements/base.txt file and I was not sure if I was allowed to.
  So I opted to perform the Sentry integration via the Github actions method which did not require editing any other files and that I would only be specifying environments and taking care of the deployment to DigitalOcean via the GitLab file.
  Here I imported my GitHub fork to GitLab and I proceeded to set up the Sentry account, AUTH_TOKEN secret in GitHub and GitHub action file. I also completed the GitLab file for the deployment to DigitalOcean.

## TROUBLESHOOTING
  
· Here I started to encounter several issues when running my first deployment tests via GitLab. At first there was an error during build which I managed to overcome with ease.
  Then on the next phase, TEST, I began to encounter several more issues having to do with environment variables. I started becoming frustrated fixing one error and proceeding to the next error and not being able to test the deployment strategy to the Docker server.
  So I decided I would try to simply build and run the project as is directly from DigitalOcean server. The build was successful and running was too.
  Unfortunately I was not able to access the webapp hosted on the server. I started thinking I had overlooked something regarding the environment variables and getting that dreaded feeling again...

## END OF LINE
  
  It was at this point I realized I was spending much more time on the project than I had originally intended as I was running into my daily work routine as well as taking time from other coding tasks and interview processes.
  It was a sad decision but I had to give up on my troubleshooting due to these constraints and leave the task in its current state.
  
  I had also been planning on editing the compose/local/django/Dockerfile but never managed to get around to it. 
