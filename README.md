# Fair & Lovely Studio: secured classroom prototype

## Firebase setup
The Firebase project URL and public web configuration are already in `config.js`. Anonymous Authentication and Realtime Database are already created.

1. Firebase > Realtime Database > Rules: replace the existing rules with contents of `database.rules.json`, then click **Publish**. These rules permit anonymous users to read votes and team work, but only to write their own vote. A team's first submitting scribe becomes the only account permitted to edit that team submission. Make sure each team chooses **one scribe on one device/browser** and keeps using that device. Others should not submit before the scribe.
2. To host without using terminal commands: create a public GitHub repository, upload *all files in this folder* to its root, then Settings > Pages > Deploy from branch > main / root. Wait for the GitHub Pages link. Firebase Authentication may need your GitHub Pages domain added to Authentication > Settings > Authorized domains.
3. Open `index.html` at the hosted website for the instructor; share the hosted `student.html` link with students. Test with a second browser.

## Critical limits
- **Instructor reset is intentionally disabled.** There is no secure instructor login yet. To start a new class, update `FL_SESSION` in `config.js` and the matching session key in Firebase rules.
- Only a designated scribe per team can edit a team's submission; this is not simultaneous multi-user editing.
- Anonymous sign-in permits extra votes via separate accounts/browsers. This is a low-stakes class poll, not a validated assessment.
- All signed-in students can read the seven team submissions and all vote values (without identity data). Do not enter sensitive student details.
- Anyone with the public student link can anonymously sign in and participate. This is suitable only for a low-stakes, supervised classroom prototype. Stronger access control would require an instructor login and team membership provisioning.
- Firebase Hosting or another HTTPS host is still required before class; the application is not yet published.
