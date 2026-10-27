# Interviewers Against You

A [Claude Code](https://claude.com/claude-code) skill for practicing tech job interviews. A panel of four interviewers studies your LinkedIn profile and the job's stack, interviews you, evaluates every answer, and ends with a hiring decision and detailed feedback.

## The panel

| Interviewer | Personality | Evaluates |
|---|---|---|
| **Senior tech lead** | A veteran of the field who wants to know whether you really understand things or just repeat what an AI told you | Technical depth, fundamentals, debugging, trade-offs |
| **Head of HR** | Warm but very careful; protects a friendly work environment | Collaboration, conflict, feedback, how you talk about other people |
| **Product owner** | Impatient; wants a fast answer to everything | Scope, features, business thinking, prioritization |
| **Team lead** | Happy with his team as it is and doesn't want you to pass. Quiet. | Hard "what would you do if..." scenarios on his team's stack |

## How it works

1. **Setup:** language (the first message is always in English), your name, your LinkedIn profile, and the job (LinkedIn post link or stack).
2. **Independent prep:** each interviewer reads your profile **on their own** and takes notes. These run as four parallel subagents, so no interviewer sees the others' notes.
3. **Huddle:** the interviewers compare notes, point out what the others missed, and plan the interview.
4. **Interview:** about 12–15 questions plus follow-ups. **All four interviewers evaluate every answer.**
5. **Deliberation:** each interviewer's verdict, the panel's decision, scores, strengths, improvements, and a study plan.

Everything is saved to `interview-sessions/<date>-<name>/` in the directory where you ran Claude Code:
`candidate.md`, `panel-notes.md` (private notes and huddle), `interview-log.md` (every answer, evaluated by all four), and `final-report.md`.

## Installation

### As a plugin (recommended)

In Claude Code:

```
/plugin marketplace add <github-user>/interviewers-against-you
/plugin install interviewers-against-you@interviewers-against-you
```

Then start the interview with `/interviewers-against-you:mock-interview`.

### Manual

Copy the skill folder into your personal skills directory:

```bash
git clone https://github.com/<github-user>/interviewers-against-you.git
cp -r interviewers-against-you/skills/mock-interview ~/.claude/skills/
```

Then start the interview with `/mock-interview`. You can also just ask, for example "I want to practice a job interview."

## About LinkedIn

LinkedIn usually blocks access to profiles when you are not logged in. If the skill can't read your profile from the link, it will ask for one of these:

- **the profile as a PDF:** on your profile page, **More → Save to PDF**, then give the file path;
- the profile text pasted into chat;
- your résumé/CV.

Public job posts (`linkedin.com/jobs/view/...`) usually load. If one doesn't, paste the job description.

## Tips

- Answer the way you would in a real interview: type the way you would speak. Don't paste answers you prepared somewhere else; the tech lead will notice.
- For a realistic experience, don't open the `interview-sessions/` folder until the interview is over.
- Type "pause" to step out of the role-play and ask something. You can end the interview at any time.
- Your profile data stays in local files on your machine. It is still sent to Claude during the session, as with any conversation.
