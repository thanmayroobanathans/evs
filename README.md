# EVS Final Exam Trainer

An adaptive practice quiz for **IACHY101 / BACHY101 Environmental Sciences (Fall 2026–27)**. It has 732 multiple-choice questions covering all six modules.

Open `index.html` in a browser, or use the GitHub Pages site. It has no build step and no dependencies, and your progress is saved in your browser.

## Modes
- **Adaptive practice:** picks the next question based on what you know and what you're about to forget.
- **Mock exam (40 Q):** questions spread across modules by syllabus share, with no feedback until the end.
- **Fix my mistakes:** only questions you've got wrong.
- **Trap drill:** questions on conflicting numbers in the notes, 20- vs 100-year values and look-alike facts. Each needs 2 correct answers in a row.
- **Unseen only:** questions you haven't answered yet.
- **Topic drill:** tap any topic bar.

## How it adapts
- **Kalman filter per topic:** the measurement model is `P(correct) = 0.25 + 0.73·σ(m)`, which includes the 4-option guess floor and a 2% slip rate. Uncertainty grows on topics you haven't practised recently, to model forgetting.
- **Thompson sampling:** chooses the topic with the most sampled marks at risk.
- **Half-life regression:** each question returns when its predicted recall drops to 90%.
- **Trap queue:** you tag each miss with a reason (didn't know it, misread, mixed up facts, number slip). Misreads, mix-ups and slips go into the trap queue.
- **Monte Carlo score prediction:** simulates 3,000 papers to estimate your chance of 40/40 and of 38 or more.
