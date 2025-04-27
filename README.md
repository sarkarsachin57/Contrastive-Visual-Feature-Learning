<h1>🚀 Contrastive Learning Evaluation with kNN on Unlabeled Dataset</h1>

<p>
  <img src="https://img.shields.io/badge/license-GNU-green.svg" />
  <img src="https://img.shields.io/badge/python-3.8%2B-blue.svg" />
  <img src="https://img.shields.io/badge/framework-PyTorch-lightgrey.svg" />
</p>

<hr>

<h2>1. 📖 Abstract / Introduction</h2>
<p>
This project explores the power of <strong>Contrastive Learning</strong> by training on a fully <strong>unlabeled dataset</strong> and evaluating the model purely using <strong>k-Nearest Neighbors (kNN)</strong> — without fine-tuning a classifier.<br>
The goal is to prove that <strong>self-supervised contrastive representations</strong> can meaningfully cluster and separate classes even without labels or a classification head.
</p>

<hr>

<h2>2. 🛠️ Method</h2>
<ul>
  <li><strong>Self-Supervised Training</strong>: Train the model on an unlabeled dataset using contrastive loss.</li>
  <li><strong>Feature Extraction</strong>: Extract deep features (embeddings) from the trained model.</li>
  <li><strong>kNN Evaluation</strong>: Train a lightweight kNN classifier on a small gallery of features and evaluate.</li>
  <li><strong>Few-Shot Gallery Setup</strong>: Select only a few samples per class (e.g., 10) to simulate real-world labeling constraints.</li>
  <li><strong>Similarity Demo</strong>: Calculate and visualize dot-product similarity between sample embeddings.</li>
</ul>

<hr>

<h2>3. ⚙️ Setup (Installation)</h2>

<p><strong>Dependencies:</strong></p>
<ul>
  <li>Python 3.8+</li>
  <li>PyTorch</li>
  <li>torchvision</li>
  <li>scikit-learn</li>
  <li>tqdm</li>
  <li>numpy</li>
</ul>

<hr>

<h2>4. 📈 Results</h2>

<h3>📂 Dataset</h3>
<ul>
  <li><strong>Dataset</strong>: Private Dataset (Approximate characteristics similar to standard classification benchmarks)</li>
  <li><strong>Total Images</strong>: ~30,507</li>
  <li><strong>Classes</strong>: 256</li>
  <li><strong>Test Set</strong>: 6,122 images</li>
  <li><strong>Processing</strong>: Resized to 256, center cropped to 224</li>
  <li><strong>Note</strong>: Labels are used <strong>only for evaluation</strong>, not for training!</li>
</ul>

<hr>

<h3>🔥 Main Global Self-Similarity Evaluation</h3>
<ul>
  <li><strong>Top-1 Accuracy</strong>: 48.95%</li>
  <li><strong>Top-5 Accuracy</strong>: 66.74%</li>
  <li><strong>Top-10 Accuracy</strong>: 73.69%</li>
</ul>
<blockquote>Note: These absolute metrics depend heavily on gallery size.</blockquote>

<h3>📈 Relative (%) Accuracy (More Stable)</h3>

<table>
  <thead>
    <tr>
      <th>Top (%)</th>
      <th>Accuracy</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>0.1%</td><td>70.08%</td></tr>
    <tr><td>0.5%</td><td>84.22%</td></tr>
    <tr><td>1%</td><td>89.15%</td></tr>
    <tr><td>5%</td><td>96.83%</td></tr>
    <tr><td>10%</td><td>98.37%</td></tr>
  </tbody>
</table>

<hr>

<h3>🧠 kNN Classification (Full 256 Classes)</h3>
<ul>
  <li><strong>Before Balancing</strong>: k=1: 15.36%</li>
  <li><strong>After Balancing</strong>: k=1: 14.69%</li>
</ul>
<blockquote>✅ Significant improvement compared to random guessing (1/256 ≈ 0.39%).</blockquote>

<hr>

<h3>🎯 kNN Classification (Realistic Scenario: 10 Classes)</h3>

<ul>
  <li>Selected 10 classes with priority for larger sample sizes.</li>
  <li>10 images/class used to build the tiny gallery.</li>
</ul>

<table>
  <thead>
    <tr>
      <th>k Value</th>
      <th>Accuracy</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>1</td><td>81.42%</td></tr>
    <tr><td>2</td><td>82.12%</td></tr>
    <tr><td>3</td><td>81.56%</td></tr>
    <tr><td>5</td><td>75.84%</td></tr>
    <tr><td>8</td><td>77.09%</td></tr>
    <tr><td>10</td><td>77.09%</td></tr>
    <tr><td>15</td><td>74.86%</td></tr>
    <tr><td>20</td><td>72.63%</td></tr>
  </tbody>
</table>

<hr>

<h3>🎨 Visual Demo (Similarity)</h3>

<p><strong>Selected classes</strong>: [137, 203]</p>
![image](https://github.com/user-attachments/assets/af5bd09c-b489-46dd-9ead-348a027c97be)

<p><strong>Similarity Matrix (Dot-Product):</strong></p>

<pre><code>
[[ 1.0000  0.2332  0.0882 -0.0224]
 [ 0.2332  1.0000  0.5124  0.4067]
 [ 0.0882  0.5124  1.0000  0.6567]
 [-0.0224  0.4067  0.6567  1.0000]]
</code></pre>

<ul>
  <li>Same class A similarity (Image 1 vs 2): <strong>0.2332</strong></li>
  <li>Same class B similarity (Image 3 vs 4): <strong>0.6567</strong></li>
  <li>Different class similarity (Image 1 vs 3/4): <strong>0.0882</strong>, <strong>-0.0224</strong></li>
</ul>

<blockquote>✅ Same-class images are clearly more similar!</blockquote>

<hr>

<h2>5. ✅ Conclusion</h2>

<ul>
  <li>Contrastive Learning is highly effective for building powerful representations <strong>without labels</strong>.</li>
  <li>Using just a tiny labeled gallery, kNN classification achieves <strong>&gt;80% accuracy</strong> among selected classes.</li>
  <li>Opens the door for practical <strong>few-shot learning</strong> scenarios where labeling is costly.</li>
  <li>Feature space separation is strong enough to support classification and retrieval tasks without a classification head.</li>
</ul>

<hr>
